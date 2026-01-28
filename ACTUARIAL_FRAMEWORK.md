# Apollo Care Actuarial Framework

<p align="center">
  <strong>CMS-Compliant Pricing, Reserves, and Risk Management</strong><br/>
  <em>Version 2.0 | January 2026</em>
</p>

---

## Table of Contents

1. [Overview](#1-overview)
2. [Industry Standards](#2-industry-standards)
3. [Apollo Governance Parameters](#3-apollo-governance-parameters)
4. [Pricing Methodology](#4-pricing-methodology)
5. [Capital Adequacy](#5-capital-adequacy)
6. [Reserve Structure](#6-reserve-structure)
7. [Risk Mitigation](#7-risk-mitigation)
8. [Day 1 Viability](#8-day-1-viability)

---

## 1. Overview

Apollo Care's actuarial framework distinguishes between:

1. **Industry Standards** — Regulatory requirements and empirical norms (fixed)
2. **Governance Parameters** — Apollo-specific values configurable by DAO

This separation ensures compliance while enabling community-driven optimization.

---

## 2. Industry Standards

### 2.1 Premium Calculation Formula

```
Gross Premium = Pure Premium / (1 - Loading Percentage)
```

| Component | Definition |
|-----------|------------|
| **Pure Premium** | Expected claims (probability × magnitude of loss) |
| **Loading Percentage** | Admin costs + reserves + profit + risk margin |

### 2.2 Objective Risk Formula

```
Objective Risk = σ / (μ√N)
```

| Variable | Definition |
|----------|------------|
| σ | Standard deviation of claims |
| μ | Expected loss |
| N | Number of covered lives |

**Key Insight**: Risk decreases with more members (law of large numbers). A pool of 10,000 has much lower objective risk than a pool of 100.

### 2.3 Medical Loss Ratio (MLR) — ACA Requirements

| Market Segment | Minimum MLR | Max Loading |
|----------------|-------------|-------------|
| Individual/Small Group | 80% | 20% |
| Large Group | 85% | 15% |

```
MLR = (Claims + Quality Improvement) / (Premiums - Taxes)
```

### 2.4 Loading Percentages by Market Size

Empirical data from Morrisey (2020):

| Market Type | Typical Loading |
|-------------|-----------------|
| Large groups (>10,000 employees) | ~4% |
| Mid-size (100-10,000) | ~15% |
| Small groups (<100) | ~34% |
| Individual market | ~50% |

### 2.5 ACA Rating Rules (Regulatory)

| Factor | Rule |
|--------|------|
| **Age** | Max 3:1 ratio (oldest to youngest adult) |
| **Tobacco** | Max 50% surcharge (1.5x factor) |
| **Location** | Geographic factors allowed |
| **Health Status** | **Prohibited** for rating |

---

## 3. Apollo Governance Parameters

### 3.1 Efficiency Targets

| Parameter | Apollo Requirement | Industry Norm | Notes |
|-----------|-------------------|---------------|-------|
| **MLR** | **90%+ (REQUIRED)** | 80-85% | Hard requirement, not target |
| Admin Load | 8% | 15-50% | Blockchain efficiency |
| Reserve Margin | 2% | Variable | Within 10% total loading |
| **Total Loading** | **≤10%** | 15-50% | Required for 90%+ MLR |

**Critical Math**: MLR = 1 - Loading
- For 90% MLR, loading must be ≤10%
- Admin (8%) + Reserve (2%) = 10% loading = **90% MLR** ✓

### 3.2 CAR Zone System

Capital Adequacy Ratio (CAR) is Apollo's on-chain solvency metric:

```
CAR = (USDC Reserves + Eligible Staked APH) / Expected Annual Claims
```

| Zone | CAR Range | Enrollment Policy | ShockFactor Limit |
|------|-----------|-------------------|-------------------|
| 🟢 **Green** | ≥150% | Unlimited | 1.0x (base) |
| 🟡 **Yellow** | 125-149% | Throttled (500/mo) | Up to 1.2x |
| 🟠 **Orange** | 100-124% | Limited (100/mo) | Up to 1.5x |
| 🔴 **Red** | <100% | Frozen | Up to 2.0x |

*These thresholds are governance parameters, not actuarial standards.*

### 3.3 ShockFactor (Special Assessment)

In mutual insurance, this is called a "special assessment" — spreading unexpected costs across members.

| Scenario | ShockFactor | Approval Required |
|----------|-------------|-------------------|
| Green zone normal | 1.0x | Automatic |
| Yellow zone stress | Up to 1.2x | Committee |
| Orange zone distress | Up to 1.5x | Committee |
| Red zone emergency | Up to 2.0x | DAO vote |

---

## 4. Pricing Methodology

### 4.1 Risk-Managed Contribution Algorithm (R-MCA)

Apollo uses CMS-compliant pricing with the following factors:

#### Age Rating (3:1 Compliance)

| Age Band | Factor | Monthly Base* |
|----------|--------|---------------|
| 0-14 | 0.765 | ~$344 |
| 15-20 | 0.833 | ~$375 |
| 21-24 | 1.000 | ~$450 |
| 25-29 | 1.004 | ~$452 |
| 30-34 | 1.135 | ~$511 |
| 35-39 | 1.259 | ~$567 |
| 40-44 | 1.427 | ~$642 |
| 45-49 | 1.600 | ~$720 |
| 50-54 | 1.786 | ~$804 |
| 55-59 | 2.230 | ~$1,004 |
| 60-64 | 2.714 | ~$1,221 |
| 64+ | 3.000 | ~$1,350 |

*Base rate varies by region and plan

#### Tobacco Surcharge

| Status | Factor |
|--------|--------|
| Non-tobacco | 1.0x |
| Tobacco user | Up to 1.5x (ACA maximum) |
| ACA Maximum | 1.5x |

### 4.2 Premium Components

```
Final Premium = Base Rate × Age Factor × Tobacco Factor × Region Factor × ShockFactor
```

| Component | Allocation |
|-----------|------------|
| Claims Reserve | 90% |
| Administration | 8% |
| Reserve Building | 2% |

### 4.3 Code Implementation

```rust
// Industry Standards (regulatory)
pub const ACA_MIN_MLR_SMALL_BPS: u16 = 8000;        // 80%
pub const ACA_MAX_AGE_RATIO: u8 = 3;                 // 3:1
pub const ACA_MAX_TOBACCO_SURCHARGE_BPS: u16 = 5000; // 50%

// Apollo Requirements (governance)
pub const APOLLO_TARGET_MLR_BPS: u16 = 9000;         // 90% REQUIRED
pub const MIN_MLR_BPS: u16 = 9000;                   // 90% minimum
pub const MAX_TOTAL_LOADING_BPS: u16 = 1000;         // 10% max loading
pub const ADMIN_LOAD_BPS: u16 = 800;                 // 8% admin
pub const RESERVE_MARGIN_BPS: u16 = 200;             // 2% reserve
pub const TARGET_CAR_BPS: u16 = 12500;               // 125%
```

---

## 5. Capital Adequacy

### 5.1 CAR Calculation

```rust
pub fn calculate_car(
    usdc_reserves: u64,
    eligible_staked_aph_value: u64,
    expected_annual_claims: u64,
) -> u16 {
    let total_capital = usdc_reserves + eligible_staked_aph_value;

    // CAR in basis points (12500 = 125%)
    (total_capital * 10000 / expected_annual_claims) as u16
}
```

### 5.2 Eligible Staked APH

Not all staked APH counts toward CAR:

| Tier | CAR Eligibility | Discount |
|------|-----------------|----------|
| Conservative | 100% | None |
| Standard | 90% | 10% haircut |
| Aggressive | 75% | 25% haircut |

**Rationale**: Higher-risk tiers have higher loss potential, so discounted for solvency purposes.

### 5.3 CAR Targets

| Metric | Target | Purpose |
|--------|--------|---------|
| Minimum CAR | 100% | Regulatory floor |
| Target CAR | 125% | Operating target |
| Optimal CAR | 150%+ | Full enrollment |

---

## 6. Reserve Structure

### 6.1 Three-Tier System

| Tier | Purpose | Target | Funding Source |
|------|---------|--------|----------------|
| **Tier 0** | Liquidity Buffer | 0-30 days claims | Premium inflow |
| **Tier 1** | Operating Reserve | 30-60 days claims | Excess premiums |
| **Tier 2** | Contingent Capital | 6+ months | Treasury + Staked APH |

### 6.2 Claims Payment Waterfall

```
Approved Claim
      │
      ▼
┌─────────────────┐
│    TIER 0       │ ← Current premium contributions
│  (Liquidity)    │
└────────┬────────┘
         │ If insufficient
         ▼
┌─────────────────┐
│    TIER 1       │ ← Operating reserve
│  (Operating)    │
└────────┬────────┘
         │ If insufficient
         ▼
┌─────────────────┐
│    TIER 2       │ ← DAO Treasury (USDC first)
│  (Contingent)   │
└────────┬────────┘
         │ If insufficient
         ▼
┌─────────────────┐
│  STAKED APH     │ ← Pro-rata liquidation (capped)
│  (Emergency)    │
└────────┬────────┘
         │ If insufficient (extreme)
         ▼
┌─────────────────┐
│  INSURANCE      │ ← DAO vote required
│  RESERVE        │
└─────────────────┘
```

### 6.3 IBNR (Incurred But Not Reported)

```
IBNR = (Average Daily Claims × Reporting Lag Days) × Development Factor
```

| Parameter | Value | Notes |
|-----------|-------|-------|
| Reporting Lag | 14-30 days | Time from service to claim |
| Development Factor | 1.15 | 15% margin for late reports |
| AI Adjustment | Variable | ML-based refinement |

---

## 7. Risk Mitigation

### 7.1 Enrollment Controls

| CAR Level | Max Enrollment | Additional Controls |
|-----------|----------------|---------------------|
| ≥150% | Unlimited | None |
| 125-149% | 500/month | Standard underwriting |
| 100-124% | 100/month | Enhanced underwriting |
| <100% | 0 | Enrollment frozen |

### 7.2 Adverse Selection Mitigations

| Control | Implementation |
|---------|----------------|
| Waiting periods | 30-day wait for non-emergency |
| Enrollment windows | Quarterly open enrollment |
| Persistency discounts | 5-10% for 12+ month members |
| Cohort monitoring | Loss ratio tracking by enrollment period |

### 7.3 Reinsurance Structure

| Layer | Attachment | Coverage | Purpose |
|-------|------------|----------|---------|
| Layer 1 (Specific) | $100K | 90% | Individual large claims |
| Layer 2 (Aggregate) | 110% loss ratio | 100% to 150% | Pool volatility |
| Layer 3 (Catastrophic) | 150% loss ratio | 100% to 300% | Black swan events |

### 7.4 Circuit Breakers

| Trigger | Action |
|---------|--------|
| CAR < 100% | Enrollment freeze |
| Daily claims > 3x average | Committee alert |
| Single claim > $25K | DAO notification |
| Staked APH liquidation | Emergency DAO session |

---

## 8. Day 1 Viability

### 8.1 Capital Structure at Launch

With $50M ICO:

| Use | Amount | % | Purpose |
|-----|--------|---|---------|
| Tier 2 Reserves | $32.5M | 65% | Contingent capital |
| Operations | $7.5M | 15% | 18-24 month runway |
| DEX Liquidity | $5M | 10% | APH/USDC trading |
| Legal/Compliance | $2.5M | 5% | Regulatory prep |
| Security/Audits | $2.5M | 5% | Smart contract audits |

### 8.2 Solvency Assessment

**Starting Position**:
- CAR at launch: Well above 150% (Green Zone)
- Reserve coverage: 6+ months (Tier 2 ICO funds)
- Reinsurance: Stop-loss at $100K attachment

### 8.3 Bootstrap Mode ($1.5M-$5M)

For smaller capital raises:

| Parameter | Bootstrap Value | Scaled Value |
|-----------|-----------------|--------------|
| Max members | 200 | Unlimited |
| Auto-approve threshold | $500 | $1,000 |
| Shock claim threshold | $25K | $100K |
| Enrollment cap | 25/month | 500/month |

### 8.4 Member Capacity Calculation

```
Expected Annual Claims per Member: $4,000-$6,000
Monthly Claims per Member: $333-$500

With $750K Tier 1 Reserve:
  Conservative: $750K / $500 = 1,500 member-months
  At 100 members: 15 months reserve runway
  At 200 members: 7.5 months reserve runway
```

---

## Summary

Apollo Care's actuarial framework:

1. **Meets or exceeds industry standards**
   - CMS-compliant rating factors
   - ACA-compliant MLR (exceeds at 90%+)

2. **Provides transparent solvency metrics**
   - On-chain CAR calculation
   - Public reserve balances

3. **Enables community governance**
   - DAO-configurable parameters
   - Committee oversight

4. **Is viable from Day 1**
   - Conservative capitalization
   - Enrollment controls
   - Multi-tier reserves

---

<p align="center">
  <strong>Actuarially sound. Community governed. Transparently operated.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*   
*Status: PUBLISHED*
