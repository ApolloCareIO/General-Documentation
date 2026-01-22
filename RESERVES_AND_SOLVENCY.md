# Apollo Care Reserves & Solvency

<p align="center">
  <strong>Three-Tier Reserve System and Capital Adequacy</strong><br/>
  <em>Version 2.0 | January 2026</em>
</p>

---

## Table of Contents

1. [Overview](#1-overview)
2. [Reserve Architecture](#2-reserve-architecture)
3. [Capital Adequacy Ratio](#3-capital-adequacy-ratio)
4. [Claims Payment Waterfall](#4-claims-payment-waterfall)
5. [Staked APH Integration](#5-staked-aph-integration)
6. [Emergency Procedures](#6-emergency-procedures)
7. [Recovery Mechanisms](#7-recovery-mechanisms)

---

## 1. Overview

### 1.1 Solvency-First Design

Apollo Care's reserve system is designed with **solvency as the primary constraint**. This means:

- Claims are paid through **rules** based logic
- Reserve requirements **gate** all distributions
- Transparency enables **real-time** monitoring (multiple backup layers)
- Community stakes provide **contingent capital**

### 1.2 Key Principle

> No distributions (staking yields, buybacks, dividends) occur unless Capital Adequacy Ratio remains above 125% post-distribution.

---

## 2. Reserve Architecture

### 2.1 Three-Tier System

```
┌─────────────────────────────────────────────────────────────────┐
│                     RESERVE ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ ┌─────────────────────────────────────────────────────────────┐ │
│ │  TIER 0: LIQUIDITY BUFFER                                   │ │
│ │  ├─ Target: 7-30 days of claims                             │ │
│ │  ├─ Funded by: Current premium inflow                       │ │
│ │  ├─ Purpose: Instant claim payouts                          │ │
│ │  └─ Status: Always liquid, never invested                   │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                              │                                  │
│                              ▼                                  │
│ ┌─────────────────────────────────────────────────────────────┐ │
│ │  TIER 1: OPERATING RESERVE                                  │ │
│ │  ├─ Target: 30-60 days of claims + IBNR margin              │ │
│ │  ├─ Funded by: Excess premiums, reserve margin              │ │
│ │  ├─ Purpose: Absorb normal claim volatility                 │ │
│ │  └─ Status: USDC, accessible within hours                   │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                              │                                  │
│                              ▼                                  │
│ ┌─────────────────────────────────────────────────────────────┐ │
│ │  TIER 2: CONTINGENT CAPITAL                                 │ │
│ │  ├─ Target: 6+ months of claims                             │ │
│ │  ├─ Funded by: DAO Treasury + Staked APH                    │ │
│ │  ├─ Purpose: Emergency backstop                             │ │
│ │  └─ Status: Requires governance or automatic triggers       │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.2 Tier Details

#### Tier 0: Liquidity Buffer

| Attribute | Value |
|-----------|-------|
| **Target** | 7-30 days average claims |
| **Source** | Premium contributions |
| **Access** | Immediate (smart contract) |
| **Investment** | None (100% liquid USDC) |
| **Replenishment** | Continuous from premiums |

#### Tier 1: Operating Reserve

| Attribute | Value |
|-----------|-------|
| **Target** | 30-60 days claims + IBNR |
| **Source** | 2% reserve margin from premiums |
| **Access** | Automatic when Tier 0 insufficient |
| **Investment** | Short-duration, low-risk only |
| **Replenishment** | Monthly from premium excess |

#### Tier 2: Contingent Capital

| Attribute | Value |
|-----------|-------|
| **Target** | 6+ months claims capacity |
| **Source** | DAO Treasury (USDC) + Staked APH |
| **Access** | Automatic triggers or DAO vote |
| **Investment** | Treasury-managed |
| **Replenishment** | ICO funds, surplus, emissions |

### 2.3 IBNR (Incurred But Not Reported)

Reserves for claims that have occurred but not yet been submitted:

```
IBNR = (Average Daily Claims × Reporting Lag Days) × Development Factor

Example:
  Average Daily Claims: $10,000
  Reporting Lag: 21 days
  Development Factor: 1.15

  IBNR = $10,000 × 21 × 1.15 = $241,500
```

---

## 3. Capital Adequacy Ratio

### 3.1 CAR Definition

```
CAR = (USDC Reserves + Eligible Staked APH Value) / Expected Annual Claims
```

### 3.2 CAR Components

| Component | Calculation |
|-----------|-------------|
| **USDC Reserves** | Tier 0 + Tier 1 + Tier 2 (USDC portion) |
| **Eligible Staked APH** | Market value × tier haircuts |
| **Expected Annual Claims** | Historical + AI forecast |

### 3.3 CAR Zones

| Zone | CAR Range | Implications |
|------|-----------|--------------|
| 🟢 **Green** | ≥150% | Full operations, unlimited enrollment |
| 🟡 **Yellow** | 125-149% | Cautious mode, throttled enrollment |
| 🟠 **Orange** | 100-124% | Restricted mode, limited enrollment |
| 🔴 **Red** | <100% | Emergency mode, enrollment frozen |

### 3.4 Zone Behaviors

```rust
pub fn get_zone_behavior(car_bps: u16) -> ZoneBehavior {
    match car_bps {
        15000.. => ZoneBehavior {
            zone: Zone::Green,
            enrollment_cap: None,
            shock_factor_limit: 10000,  // 1.0x
            distributions_allowed: true,
        },
        12500..=14999 => ZoneBehavior {
            zone: Zone::Yellow,
            enrollment_cap: Some(500),
            shock_factor_limit: 12000,  // 1.2x
            distributions_allowed: true,
        },
        10000..=12499 => ZoneBehavior {
            zone: Zone::Orange,
            enrollment_cap: Some(100),
            shock_factor_limit: 15000,  // 1.5x
            distributions_allowed: false,
        },
        _ => ZoneBehavior {
            zone: Zone::Red,
            enrollment_cap: Some(0),
            shock_factor_limit: 20000,  // 2.0x
            distributions_allowed: false,
        },
    }
}
```

---

## 4. Claims Payment Waterfall

### 4.1 Payment Priority

When a claim is approved, funds are sourced in strict order:

```
APPROVED CLAIM: $5,000
        │
        ▼
┌───────────────────────┐
│ STEP 1: TIER 0        │
│ Current premiums      │
│ Available: $3,000     │ ← Use $3,000
└───────────┬───────────┘
            │ Need: $2,000 more
            ▼
┌───────────────────────┐
│ STEP 2: TIER 1        │
│ Operating reserve     │
│ Available: $50,000    │ ← Use $2,000
└───────────┬───────────┘
            │ Claim fully funded
            ▼
       PAYMENT SENT
```

### 4.2 Full Waterfall

| Step | Source | When Used |
|------|--------|-----------|
| 1 | Tier 0 (Liquidity) | First for all claims |
| 2 | Tier 1 (Operating) | When Tier 0 insufficient |
| 3 | Credit Line (if available) | Bridge financing |
| 4 | Tier 2 Treasury (USDC) | When Tier 1 insufficient |
| 5 | Staked APH Liquidation | Emergency only |
| 6 | Insurance Reserve Tokens | Last resort (DAO vote) |

### 4.3 Credit Line Integration

For liquidity management, Apollo may maintain a credit facility:

| Attribute | Value |
|-----------|-------|
| **Size** | ~1 month of claims |
| **Purpose** | Bridge unexpected spikes |
| **Repayment** | From subsequent premiums |
| **Collateral** | DAO Treasury |

---

## 5. Staked APH Integration

### 5.1 Role in Normal Operations

During peacetime, staked APH:
- Counts toward CAR calculation
- Never actually liquidated
- Earns yields for backing
- Improves solvency metrics

### 5.2 Tier Haircuts

Not all staked APH counts equally:

| Staking Tier | CAR Credit | Rationale |
|--------------|------------|-----------|
| Conservative | 100% | Lowest loss cap (2%) |
| Standard | 90% | Medium loss cap (5%) |
| Aggressive | 75% | Highest loss cap (10%) |

### 5.3 Liquidation Mechanics

When Tier 2 USDC exhausted and claims remain:

```
LIQUIDATION TRIGGER
        │
        ▼
┌────────────────────────────────────────────────────────────────┐
│  LIQUIDATION PARAMETERS                                        │
│  ├─ Amount needed: $X                                          │
│  ├─ Total staked APH value: $Y                                 │
│  ├─ Per-tier caps: Conservative 2%, Standard 5%, Aggressive 10%│
│  └─ Maximum single-event liquidation: Lesser of X or caps      │
└────────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────┐
│  TWAP EXECUTION (24-72 hours)                                 │
│  ├─ Spread sales over time                                    │
│  ├─ 15% slippage circuit breaker                              │
│  ├─ Pro-rata across all stakers in tier                       │
│  └─ Proceeds deposited to claims fund                         │
└───────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────┐
│  GOVERNANCE ALERT                                             │
│  ├─ Emergency notification to all holders                     │
│  ├─ Automatic DAO meeting triggered                           │
│  └─ Post-mortem and recovery planning                         │
└───────────────────────────────────────────────────────────────┘
```

### 5.4 Loss Distribution Example

| Staker | Tier | Staked | Max Loss | Actual Loss* |
|--------|------|--------|----------|--------------|
| Alice | Conservative | 10,000 APH | 200 APH (2%) | 150 APH |
| Bob | Standard | 10,000 APH | 500 APH (5%) | 375 APH |
| Carol | Aggressive | 10,000 APH | 1,000 APH (10%) | 750 APH |

*If total needed = 75% of caps

---

## 6. Emergency Procedures

### 6.1 Automatic Triggers

| Trigger | Condition | Action |
|---------|-----------|--------|
| **Yellow Alert** | CAR < 150% | Throttle enrollment |
| **Orange Alert** | CAR < 125% | Limit enrollment, pause distributions |
| **Red Alert** | CAR < 100% | Freeze enrollment, emergency DAO |
| **Critical** | Tier 2 depleted | Staked APH liquidation |

### 6.2 Emergency DAO Session

When critical thresholds breached:

1. **Automatic notification** to all APH holders
2. **48-hour emergency vote** period
3. **Options presented**:
   - Increase ShockFactor (raise premiums)
   - Execute Insurance Reserve token sale
   - Seek external capital
   - Temporary coverage modifications

### 6.3 Run-Off Reserve

If Apollo ever ceases operations:

| Component | Purpose |
|-----------|---------|
| **Run-off fund** | Pay existing claims through run-out |
| **IBNR completion** | Cover claims not yet reported |
| **Administration** | Orderly wind-down operations |

---

## 7. Recovery Mechanisms

### 7.1 Post-Crisis Recovery

After any reserve drawdown event:

```
CRISIS RESOLVED
        │
        ▼
┌───────────────────────────────────────────────────────────────┐
│  RECOVERY PHASE 1: STABILIZATION                              │
│  ├─ ShockFactor elevated (higher premiums)                    │
│  ├─ Enrollment restricted                                     │
│  └─ Distributions paused                                      │
└───────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────┐
│  RECOVERY PHASE 2: REPLENISHMENT                              │
│  ├─ Reserves rebuilt from premium excess                      │
│  ├─ Potential fundraising (token sale, partnerships)          │
│  └─ Staker compensation plan (if liquidated)                  │
└───────────────────────────────────────────────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────┐
│  RECOVERY PHASE 3: NORMALIZATION                              │
│  ├─ CAR returns to Green Zone                                 │
│  ├─ ShockFactor normalized                                    │
│  ├─ Enrollment restrictions lifted                            │
│  └─ Distributions resume                                      │
└───────────────────────────────────────────────────────────────┘
```

### 7.2 Staker Recovery Options

If stakers lost tokens in liquidation:

| Option | Description |
|--------|-------------|
| **Priority Yields** | First claim on future surplus |
| **Recovery Tokens** | Special allocation from Community Fund |
| **Premium Share Boost** | Temporary increased yield rate |

### 7.3 System Resilience

Multiple layers ensure valid claims are always paid:

| Layer | Protection |
|-------|------------|
| 1 | Premium inflow (Tier 0) |
| 2 | Operating reserves (Tier 1) |
| 3 | Credit facilities |
| 4 | DAO Treasury (Tier 2 USDC) |
| 5 | Staked APH (capped liquidation) |
| 6 | Insurance Reserve tokens |
| 7 | Governance emergency measures |

---

## Summary

Apollo Care's reserve system provides:

| Feature | Benefit |
|---------|---------|
| **Three-tier reserves** | Multiple protection layers |
| **Real-time CAR** | Transparent solvency |
| **Automatic triggers** | Proactive risk management |
| **Staker backing** | Community-funded capital |
| **Recovery mechanisms** | Path back to stability |

**Core Promise**: Through this multi-layered system, **valid claims are always paid**.

---

<p align="center">
  <strong>Reserves on-chain. Solvency transparent. Claims always paid.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*  
*Status: PUBLISHED*
