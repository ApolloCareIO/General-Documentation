# Apollo Care Tokenomics

<p align="center">
  <img src="https://info.apollocare.io/assets/apollo-logo-new-C-ImmPTU.png" alt="Apollo Care Logo" width="120"/>
</p>

<p align="center">
  <strong>$APH Token Economics Technical Paper</strong><br/>
  <em>Version 2.0 | January 2025</em>
</p>

---

## Table of Contents

1. [Overview](#1-overview)
2. [Token Fundamentals](#2-token-fundamentals)
3. [Token Allocation](#3-token-allocation)
4. [Token Utility](#4-token-utility)
5. [Staking Mechanics](#5-staking-mechanics)
6. [Value Accrual](#6-value-accrual)
7. [Reserve Integration](#7-reserve-integration)
8. [Community Incentives](#8-community-incentives)
9. [Token-2022 Features](#9-token-2022-features)
10. [Economic Security](#10-economic-security)

---

## 1. Overview

### 1.1 Design Philosophy

Apollo Care's tokenomics separates two distinct participant classes:

| **Coverage Members** | **Token Holders** |
|---------------------|-------------------|
| Pay monthly USDC premiums | Stake APH for capital backing |
| Receive health coverage | Participate in governance |
| No token ownership required | Earn yields from operations |
| Primary beneficiaries of MLR | Provide contingent capital |

**Key Principle**: Holding $APH is **not required** for health coverage. Members join and maintain coverage by paying premiums in stablecoins (USDC) with no obligation to purchase tokens.

### 1.2 Token Purpose

$APH serves as Apollo's **coordination instrument**:

1. **Governance**: Empower community decision-making
2. **Capital Backing**: Enable decentralized underwriting via staking
3. **Incentive Alignment**: Connect platform success with token holder value
4. **Protocol Sustainability**: Fund operations through transfer fees

### 1.3 Legal Structure

Apollo Protocol DAO LLC ensures:
- Regulatory compliance with U.S. norms
- Limited liability for participants
- Legal enforceability of smart contracts
- Clear ownership and governance structure

---

## 2. Token Fundamentals

### 2.1 Specifications

| Property | Value |
|----------|-------|
| **Name** | Apollo Care |
| **Symbol** | APH |
| **Network** | Solana |
| **Program** | Token-2022 (Token Extensions) |
| **Contract** | `6S3T6f1mmhxQWKR1gMiZR1SZLpu396jnnRMGqAZUj3Qj` |
| **Decimals** | 9 |
| **Total Supply** | 1,000,000,000 APH |
| **Supply Type** | Fixed (no inflation) |

### 2.2 Token-2022 Extensions

APH was minted as a **Token-2022** token from day one with built-in extensions:

| Extension | Status | Configuration |
|-----------|--------|---------------|
| **Transfer Fee** | Active | 2% fee rate (0% during presale) |
| **Max Fee Cap** | Active | 200,000 APH per transaction |
| **Metadata** | Active | On-chain token metadata |

The transfer fee config authority can update the fee rate without redeploying the token.

---

## 3. Token Allocation

### 3.1 Distribution Summary

| Category | Percentage | Amount | Purpose |
|----------|------------|--------|---------|
| **Community & Ecosystem** | 47% | 470,000,000 APH | Growth, incentives, partnerships |
| **Core Team & Advisors** | 22% | 220,000,000 APH | Founding team, advisors |
| **Seed & Strategic** | 10% | 100,000,000 APH | Early backers |
| **Insurance Reserve** | 10% | 100,000,000 APH | Emergency capital backstop |
| **Liquidity & Exchanges** | 6% | 60,000,000 APH | DEX pools, market making |
| **Operations** | 5% | 50,000,000 APH | Platform costs |
| **Total** | **100%** | **1,000,000,000 APH** | |

### 3.2 Allocation Details

#### Community & Ecosystem Fund (47% — 470M APH)

The largest allocation, underlining Apollo's community-first approach:

- Member recruitment rewards
- Governance participation incentives
- Liquidity provision programs
- Developer grants
- Marketing and partnerships

**Distribution**: Managed by DAO with gradual release schedules to prevent oversupply.

#### Core Team & Advisors (22% — 220M APH)

Rewards those building the platform while ensuring commitment:

- Multi-year vesting schedules
- Cliff periods before first unlock
- Performance-based acceleration options

**Vesting**: Tokens unlock gradually over 3-4 years, not immediately tradable.

#### Seed & Strategic Investors (10% — 100M APH)

Early backers who provided initial funding:

- Subject to vesting
- Supports early platform development
- Strategic value-add requirements

#### Insurance Reserve (10% — 100M APH)

Emergency capital backstop:

- Held by DAO treasury
- Only deployed in extreme scenarios
- DAO vote required for utilization
- Provides additional solvency buffer

#### Liquidity & Exchanges (6% — 60M APH)

Ensures healthy token market:

- DEX liquidity pools (APH/USDC, APH/SOL)
- Market making partnerships
- Exchange listings

#### Operations (5% — 50M APH)

Platform operational costs:

- Development expenses
- Infrastructure costs
- Legal and compliance
- Marketing campaigns

### 3.3 ICO Allocation

Target ICO: **$1.5 - 50M**

| Use | Amount | % | Purpose |
|-----|--------|---|---------|
| Tier 2 Reserves | $32.5M | 65% | Contingent capital |
| Operations Runway | $7.5M | 15% | 18-24 month ops |
| DEX Liquidity | $5M | 10% | APH/USDC pools |
| Legal/Compliance | $2.5M | 5% | Regulatory prep |
| Security/Audits | $2.5M | 5% | Smart contract audits |

---

## 4. Token Utility

### 4.1 Core Utilities

$APH provides four primary utilities:

#### 1. Governance

| Function | Description |
|----------|-------------|
| **Proposal Voting** | Vote on coverage policies, rates, upgrades |
| **Committee Elections** | Elect Claims, Risk, Treasury committees |
| **Treasury Allocation** | Direct surplus utilization |
| **Protocol Changes** | Approve smart contract updates |

**Voting Power**: 1 APH = 1 vote

#### 2. Capital Staking

Stake APH to backstop the insurance pool and earn yield:

| Benefit | Description |
|---------|-------------|
| **Yield Earning** | Share of member premiums |
| **Governance Weight** | Staked tokens often carry higher weight |
| **Reserve Backing** | Staked APH counts toward CAR |

#### 3. Community Incentives

Earn APH through positive actions:

- Referral rewards
- Wellness program participation
- Governance participation
- Liquidity provision

#### 4. Value Accrual

When Apollo succeeds, token holders benefit:

- Buyback & burn programs
- Dividend distributions
- Treasury growth

### 4.2 What APH is NOT

**APH is NOT required for**:
- ❌ Health coverage (pay USDC premiums only)
- ❌ Filing claims
- ❌ Receiving claim payments
- ❌ Basic member benefits

---

## 5. Staking Mechanics

### 5.1 Three-Tier Staking System

Apollo offers differentiated staking tiers based on risk appetite:

| Tier | APY Range | Lock Period | Description |
|------|-----------|-------------|-------------|
| 🛡️ **Conservative** | 3-5% | 30 days | Low risk, stable returns |
| ⚖️ **Standard** | 6-8% | 5% | Balanced risk/reward |
| 🔥 **Aggressive** | 10-15% | 180 days | Higher risk, higher reward |

### 5.2 How Staking Works

```
┌───────────────────────────────────────────────────┐
│                    STAKING FLOW                   │
├───────────────────────────────────────────────────┤
│                                                   │
│                     APH Holder                    │
│                         │                         │
│                         ▼                         │
│  ┌────────────────────────────────────────────┐   │
│  │  SELECT TIER                               │   │
│  │  • Conservative (3-5% APY)                 │   │
│  │  • Standard (6-8% APY)                     │   │
│  │  • Aggressive (10-15% APY)                 │   │
│  └──────────────────────┬─────────────────────┘   │
│                         │                         │
│                         ▼                         │
│  ┌─────────────────────────────────────────────┐  │
│  │  LOCK TOKENS                                │  │
│  │  • Minimum lock period per tier             │  │
│  │  • Tokens count toward CAR                  │  │
│  │  • Can't withdraw during lock               │  │
│  └──────────────────────┬──────────────────────┘  │
│                         │                         │
│                         ▼                         │
│  ┌─────────────────────────────────────────────┐  │
│  │  EARN REWARDS                               │  │
│  │  • Share of premium revenue                 │  │
│  │  • Paid in USDC and/or APH                  │  │
│  │  • Distributed periodically                 │  │
│  └──────────────────────┬──────────────────────┘  │
│                         │                         │
│                         ▼                         │
│  ┌─────────────────────────────────────────────┐  │
│  │  LOSS EXPOSURE (if reserves depleted)       │  │
│  │  • Capped at tier maximum                   │  │
│  │  • Pro-rata across stakers                  │  │
│  │  • TWAP liquidation prevents dump           │  │
│  └─────────────────────────────────────────────┘  │
│                                                   │
└───────────────────────────────────────────────────┘
```

### 5.3 Yield Sources

Staking yields come from multiple sources:

| Source | Description |
|--------|-------------|
| **Premium Share** | Portion of member USDC premiums |
| **Token Emissions** | From Community Fund (declining over time) |
| **Protocol Revenue** | Transfer fees, treasury investments |

### 5.4 Loss Mechanics

In extreme scenarios where reserves are depleted:

1. **Loss Cap**: Maximum loss per tier is enforced
2. **Pro-Rata**: Losses spread across all stakers in tier
3. **TWAP Liquidation**: 24-72 hour window prevents market dumps
4. **Circuit Breaker**: 15% slippage limit per period

**Example**: Conservative tier staker with 10,000 APH can lose maximum 200 APH (2%) even in catastrophic scenarios.

---

## 6. Value Accrual

### 6.1 Surplus Utilization

When Apollo operates profitably (claims < premiums), surplus is community capital:

```
                   SURPLUS ALLOCATION
                          │
         ┌────────────────┼────────────────┐
         │                │                │
         ▼                ▼                ▼
    ┌─────────┐     ┌──────────┐    ┌──────────┐
    │ RESERVE │     │ BUYBACK  │    │ DIVIDEND │
    │ GROWTH  │     │ & BURN   │    │ & REBATE │
    └─────────┘     └──────────┘    └──────────┘
    Priority 1      Priority 2      Priority 3
```

### 6.2 Buyback & Burn

**Mechanism**:
1. DAO votes to allocate surplus for buyback
2. Protocol buys APH on open market
3. Purchased tokens sent to burn address
4. Circulating supply permanently reduced

**Impact**:
- Deflationary pressure on supply
- Each remaining token represents larger share
- Value accrues to all holders equally

**Constraints**:
- Only if CAR remains >125% post-buyback
- Maximum % of surplus allocated (DAO sets)
- TWAP execution to minimize market impact

### 6.3 Dividends & Rebates

**Staker Dividends**:
- One-time bonus in USDC or APH
- Proportional to stake amount and duration
- Rewards commitment to platform

**Member Rebates**:
- Premium credits for loyal members
- Percentage refund on premiums paid
- Rewards healthy behavior and low claims

### 6.4 Value Alignment

| If Apollo Succeeds... | Token Holders Get... |
|----------------------|---------------------|
| More members join | Larger premium pool for staking yields |
| Lower than expected claims | Surplus for buybacks/dividends |
| Efficient operations | Higher effective yields |
| Reserve growth | Stronger CAR, lower risk |

---

## 7. Reserve Integration

### 7.1 Three-Tier Reserve System

| Tier | Purpose | Funding | Target |
|------|---------|---------|--------|
| **Tier 0** | Liquidity Buffer | Premiums | 7-30 days claims |
| **Tier 1** | Operating Reserve | Excess premiums | 30-60 days claims |
| **Tier 2** | Contingent Capital | Treasury + Staked APH | 6+ months |

### 7.2 Claims Payment Waterfall

```
CLAIM APPROVED
      │
      ▼
┌───────────────┐
│   TIER 0      │ ◀── Current premium inflow
└───────┬───────┘
        │ (if insufficient)
        ▼
┌───────────────┐
│   TIER 1      │ ◀── Operating reserve
└───────┬───────┘
        │ (if insufficient)
        ▼
┌───────────────┐
│   TIER 2      │ ◀── DAO Treasury (USDC)
└───────┬───────┘
        │ (if insufficient)
        ▼
┌───────────────┐
│  STAKED APH   │ ◀── Liquidation (capped)
└───────┬───────┘
        │ (extreme scenarios only)
        ▼
┌───────────────┐
│ INSURANCE     │ ◀── Insurance Reserve tokens
│ RESERVE       │     (DAO vote required)
└───────────────┘
```

### 7.3 Role of Staked APH

**In Normal Operations**:
- Staked APH counts toward CAR calculation
- Improves solvency metrics
- Never actually liquidated
- Earns yields for backing

**In Stress Scenarios**:
- Only tapped after Tier 0, 1, and 2 USDC exhausted
- Liquidation capped per tier (2-10%)
- TWAP execution over 24-72 hours
- Pro-rata across all stakers

### 7.4 Insurance Reserve Tokens

The 100M APH insurance reserve serves as ultimate backstop:

- Held by DAO, not circulating
- Can be sold to raise emergency USDC
- Dilutes supply but prevents insolvency
- Only deployed by DAO supermajority vote

---

## 8. Community Incentives

### 8.1 Programs Funded by Community Fund

The 47% Community & Ecosystem Fund powers growth:

#### Liquidity Mining

| Program | Purpose | APH Allocated |
|---------|---------|---------------|
| DEX Liquidity | Reward LP providers | Variable |
| Launch Boost | Bootstrap initial liquidity | Fixed allocation |

#### Referral Rewards

| Action | Reward |
|--------|--------|
| Refer new member | APH tokens on enrollment |
| Referred member stays 6+ months | Bonus reward |
| High-value referral (healthy demographic) | Enhanced reward |

#### Wellness Incentives

| Activity | Potential Reward |
|----------|-----------------|
| Annual health screening | APH tokens |
| Fitness goals (opt-in tracked) | APH tokens |
| Preventive care completion | APH tokens |

#### Governance Participation

| Action | Reward |
|--------|--------|
| Vote on proposal | Small APH stipend |
| Submit successful proposal | APH grant |
| Committee service | APH compensation |

### 8.2 Important Distinctions

These incentives are:
- **Separate from coverage** (no effect on claims eligibility)
- **Separate from staking** (different reward mechanism)
- **Gamified bonuses** (not contractual obligations)
- **Discretionary** (DAO controls parameters)

---

## 9. Token-2022 Features

### 9.1 Transfer Fee Extension

**Configuration**:
```
Fee Rate: 2% (200 basis points)
Max Fee: 200,000 APH per transaction
Status: 0% during presale → 2% post-launch
```

**Benefits**:
- Sustainable protocol funding
- Discourages excessive speculation
- Funds ongoing development
- Can be adjusted by governance

### 9.2 Fee Destination

Transfer fees are collected in a protocol-controlled account:
- Used for protocol sustainability
- DAO votes on allocation
- Can fund buybacks, development, or operations

### 9.3 Presale Exemption

During presale phase:
- Fee rate set to 0%
- Early supporters not penalized
- Fee activated after token launch
- Advance notice provided

---

## 10. Economic Security

### 10.1 Capital Gating

All value distributions are gated by solvency requirements:

```rust
// Pseudocode: Gated distribution
function distributeValue() {
    currentCAR = getCapitalAdequacyRatio();

    if (currentCAR >= 125%) {
        // Safe to distribute
        executeDistribution();
    } else {
        // Retain in reserves
        emit DistributionWithheld(currentCAR);
    }
}
```

### 10.2 Circuit Breakers

| Mechanism | Trigger | Action |
|-----------|---------|--------|
| **Enrollment Freeze** | CAR < 100% | No new members |
| **Staking Pause** | Extreme market volatility | Prevent withdrawals |
| **Liquidation Limit** | Per-period cap | Max 15% slippage |
| **Emergency Pause** | Governance decision | Halt all operations |

### 10.3 Vesting Schedules

Long-term alignment through vesting:

| Holder Class | Vesting Period | Cliff |
|-------------|----------------|-------|
| Team | 4 years | 1 year |
| Advisors | 2 years | 6 months |
| Seed Investors | 18 months | 6 months |
| Community Fund | Released by DAO | N/A |

### 10.4 Anti-Manipulation

- **TWAP Liquidations**: Spread sales over time
- **Slippage Limits**: Prevent flash crashes
- **Governance Timelocks**: Prevent rushed decisions
- **Multi-Sig Treasury**: Prevent single point of failure

---

## Summary

### Token Quick Facts

| Property | Value |
|----------|-------|
| Total Supply | 1,000,000,000 APH |
| Largest Allocation | Community Fund (47%) |
| Staking APY | 3-15% (by tier) |
| Transfer Fee | 2% (post-presale) |
| Governance | 1 token = 1 vote |

### Key Principles

1. **Coverage ≠ Token Ownership**: Health coverage via USDC premiums only
2. **Token = Governance + Staking**: APH for participation and capital backing
3. **Community First**: 47% to community programs
4. **Sustainable Economics**: Transfer fees fund operations
5. **Aligned Incentives**: Success benefits all stakeholders

---

<p align="center">
  <strong>$APH: Healthcare coverage by the people, for the people.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*  
*Status: PUBLISHED*
