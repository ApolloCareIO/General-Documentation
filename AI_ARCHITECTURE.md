# Apollo Care AI Architecture

<p align="center">
  <img src="https://info.apollocare.io/assets/apollo-logo-new-C-ImmPTU.png" alt="Apollo Care Logo" width="120"/>
</p>

<p align="center">
  <strong>AI-Optimized Claims Processing & Fraud Detection</strong><br/>
  <em>Version 2.0 | January 2026</em>
</p>

---

## Table of Contents

1. [Overview](#1-overview)
2. [Design Principles](#2-design-principles)
3. [Three-Tier Claims Processing](#3-three-tier-claims-processing)
4. [AI Models](#4-ai-models)
5. [Fraud Detection](#5-fraud-detection)
6. [Price Validation](#6-price-validation)
7. [Oracle Architecture](#7-oracle-architecture)
8. [Model Governance](#8-model-governance)
9. [Privacy & Security](#9-privacy--security)
10. [Future Roadmap](#10-future-roadmap)

---

## 1. Overview

### 1.1 AI First

Apollo Care Protocol is designed from the ground up with AI/ML integration first, and not as an afterthought. This enables:

- **90%+ Medical Loss Ratio** through automated processing
- **Minutes-not-weeks** claims resolution
- **Fraud prevention** at scale
- **Fair pricing** via reference databases

### 1.2 The AI Advantage

| Traditional Insurance | Apollo AI-Powered |
|----------------------|-------------------|
| Manual claims review | Automated triage |
| Days/weeks processing | Minutes processing |
| Reactive fraud detection | Proactive pattern detection |
| Hidden pricing | Transparent reference pricing |
| Human bias | Algorithmic consistency |

### 1.3 Architecture Philosophy

```
┌───────────────────────────────────────────────────────────────┐
│                    DATA FLOW ARCHITECTURE                     │
├───────────────────────────────────────────────────────────────┤
│                                                               │
│  ┌──────────────┐     ┌──────────────┐     ┌────────────────┐ │
│  │   On-Chain   │────▶│  Event Logs  │────▶│ ML Feature     │ │
│  │ Transactions │     │  (Indexed)   │     │ Pipeline       │ │
│  └──────────────┘     └──────────────┘     └───────┬────────┘ │
│                                                     │         │
│                                                     ▼         │
│  ┌────────────────────────────────────────────────────────┐   │
│  │                    ML MODEL LAYERS                     │   │
│  ├──────────────────┬──────────────────┬──────────────────┤   │
│  │  Claims Triage   │ Fraud Detection  │ Dynamic Pricing  │   │
│  │  (XGBoost/NN)    │ (Anomaly Det.)   │ (Gradient Boost) │   │
│  └──────────────────┴──────────────────┴──────────────────┘   │
│                              │                                │
│                              ▼                                │
│  ┌────────────────────────────────────────────────────────┐   │
│  │                 CLAIMS ORACLE PROGRAM                  │   │
│  │        (Verifiable AI decisions recorded on-chain)     │   │
│  └────────────────────────────────────────────────────────┘   │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

---

## 2. Design Principles

### 2.1 Data-First Architecture

Every transaction, claim, and member interaction generates structured data that feeds ML pipelines:

| Data Source | Features Generated |
|-------------|-------------------|
| Member enrollment | Demographics, tenure, plan type |
| Premium payments | Payment history, consistency |
| Claims submissions | Amount, frequency, categories |
| Provider interactions | Provider patterns, pricing |
| Claim outcomes | Approval rates, appeals |

### 2.2 Verifiable Decisions

All AI decisions are:
- **Recorded on-chain** with model version
- **Reproducible** via feature hash
- **Auditable** by governance
- **Overridable** by committee

### 2.3 Human-in-the-Loop

AI augments, not replaces, human judgment:
- Fast-lane: Full automation
- AI Review: AI recommends, humans oversee
- Committee: AI provides analysis, humans decide

---

## 3. Three-Tier Claims Processing

### 3.1 Processing Tiers

```
┌─────────────────────────────────────────────────────────────────┐
│                      CLAIMS SUBMISSION                          │
│                            ↓                                    │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │  TIER 1: FAST-LANE AUTO-APPROVAL                           │ │
│  │  • Claims < $500 (bootstrap) / $1,000 (scaled)             │ │
│  │  • Eligible categories: primary care, generic Rx, labs     │ │
│  │  • Member in good standing                                 │ │
│  │  • No fraud flags (score < 20)                             │ │
│  │  → INSTANT PAYOUT (seconds)                                │ │
│  └────────────────────────────────────────────────────────────┘ │
│                            ↓ (if not fast-lane)                 │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │  TIER 2: AI-ASSISTED TRIAGE                                │ │
│  │  • Claims $500-$5,000                                      │ │
│  │  • ML fraud scoring (0-100 risk score)                     │ │
│  │  • Price reasonableness check (vs UCR database)            │ │
│  │  • Document validation (OCR + verification)                │ │
│  │  → AUTO-APPROVE if score < 30 (minutes)                    │ │
│  │  → FLAG for review if score 30-70                          │ │
│  │  → ESCALATE if score > 70                                  │ │
│  └────────────────────────────────────────────────────────────┘ │
│                            ↓ (if flagged/escalated)             │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │  TIER 3: COMMITTEE/DAO REVIEW                              │ │
│  │  • Claims >$5,000 or flagged by AI                         │ │
│  │  • Claims Committee (2+ attestations required)             │ │
│  │  • 48-hour resolution target                               │ │
│  │  • DAO vote for shock claims (>$25K)                       │ │
│  │  → HUMAN DECISION (1-7 days)                               │ │
│  └────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 Decision Paths

```rust
pub enum ClaimDecisionPath {
    // Tier 1: Fast-Lane Auto-Approval (<$500, high confidence)
    FastLane {
        ai_confidence: u16,      // basis points (9500 = 95%)
        fraud_score: u16,        // lower is better
        auto_approved: bool,
    },

    // Tier 2: AI-Assisted Review ($500-$5,000)
    AiReview {
        ai_recommendation: ClaimVerdict,
        confidence: u16,
        fraud_indicators: Vec<FraudFlag>,
        requires_human: bool,
    },

    // Tier 3: Committee Review (>$5,000 or flagged)
    CommitteeReview {
        ai_analysis: ClaimAnalysis,
        committee_votes: Vec<Vote>,
        final_decision: ClaimVerdict,
    },
}
```

### 3.3 Processing Latency Targets

| Tier | Target Latency | Confidence Required |
|------|---------------|---------------------|
| Fast-Lane | <100ms | 95%+ |
| AI Review | <24 hours | 85%+ |
| Committee | 3-5 business days | N/A |

---

## 4. AI Models

### 4.1 Claims Triage Model

**Purpose**: Route claims to appropriate processing tier

**Architecture**:
- XGBoost ensemble with 500 trees
- Deep neural network for complex patterns
- Fallback rules for edge cases

**Features**:

| Feature | Type | Description |
|---------|------|-------------|
| claim_amount | float | Normalized claim amount |
| member_tenure_days | int | Days since enrollment |
| member_claims_ytd | int | Claims count this year |
| member_claims_total_ytd | float | Total claims $ this year |
| provider_claim_count | int | Provider's claim volume |
| provider_avg_approval_rate | float | Historical approval rate |
| diagnosis_risk_score | float | ICD-10 based risk |
| service_type | categorical | Office visit, ER, surgery, etc. |
| hour_of_submission | int | Time patterns |
| day_of_week | int | Day patterns |

**Output**: Tier classification + confidence score

### 4.2 Fraud Detection Model

**Purpose**: Identify potentially fraudulent claims

**Architecture**:
- Isolation Forest for anomaly detection
- Graph Neural Network for provider-member relationships
- LSTM for temporal pattern detection

**Fraud Indicators**:

| Flag | Description | Weight |
|------|-------------|--------|
| UnusualClaimVolume | Statistical outlier in frequency | High |
| ProviderPatternAnomaly | Provider behavior change | Medium |
| UpcodingIndicators | Systematic billing inflation | High |
| PhantomBilling | Services potentially not rendered | Critical |
| UnbundlingPattern | Splitting procedures for higher reimbursement | Medium |
| IdentityRisk | Member identity concerns | High |
| GeographicAnomaly | Impossible travel patterns | Medium |
| TemporalAnomaly | Unusual timing patterns | Low |

### 4.3 Dynamic Pricing Model

**Purpose**: Real-time premium adjustments based on pool risk

**Architecture**:
- Gradient Boosting for base rate prediction
- Time series forecasting for claims trends
- Cohort analysis for adverse selection detection

**ShockFactor Calculation**:

```rust
pub fn calculate_shock_factor(
    pool_metrics: &PoolMetrics,
    ai_forecast: &ClaimsForecast,
) -> u16 {
    // Base: 10000 = 1.0x (no adjustment)
    let mut shock_factor: u16 = 10000;

    // CAR-based adjustment
    if pool_metrics.car < 12500 {  // Below 125%
        shock_factor += 500;  // +5% per 25% under target
    }

    // AI forecast adjustment
    if ai_forecast.next_month_claims > pool_metrics.expected_claims * 110 / 100 {
        let overage = (ai_forecast.next_month_claims - pool_metrics.expected_claims)
            * 100 / pool_metrics.expected_claims;
        shock_factor += overage as u16 * 10;
    }

    // Cap at 2.0x (20000 bps)
    shock_factor.min(20000)
}
```

### 4.4 IBNR Estimation Model

**Purpose**: Incurred But Not Reported reserve calculation

**Formula**:
```
IBNR = (Average Daily Claims × Reporting Lag Days) × 1.15 Development Factor × AI Adjustment
```

**AI Adjustment**: Machine learning refines the development factor based on:
- Historical claim patterns
- Seasonal variations
- Member cohort behavior
- Economic conditions

---

## 5. Fraud Detection

### 5.1 Multi-Layer Defense

```
┌─────────────────────────────────────────────────────────────┐
│                   FRAUD DETECTION LAYERS                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Layer 1: REAL-TIME SCREENING                               │
│  ├─ Duplicate claim detection                               │
│  ├─ Basic eligibility checks                                │
│  └─ Known bad actor database                                │
│                                                             │
│  Layer 2: ML PATTERN DETECTION                              │
│  ├─ Anomaly scoring (Isolation Forest)                      │
│  ├─ Provider network analysis (GNN)                         │
│  └─ Temporal patterns (LSTM)                                │
│                                                             │
│  Layer 3: HUMAN INVESTIGATION                               │
│  ├─ Risk Committee review                                   │
│  ├─ Claims Committee escalation                             │
│  └─ DAO-level decisions                                     │
│                                                             │
│  Layer 4: POST-PAYMENT AUDIT                                │
│  ├─ Batch analysis of paid claims                           │
│  ├─ Provider billing pattern review                         │
│  └─ Member utilization analysis                             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 5.2 Fast-Lane Abuse Prevention

```rust
pub struct FastLaneTracker {
    /// Member being tracked
    pub member: Pubkey,

    /// Rolling 30-day fast-lane claims
    pub claims_30d: u16,

    /// Rolling 90-day fast-lane claims
    pub claims_90d: u16,

    /// Total fast-lane amount 30d (USDC)
    pub amount_30d: u64,

    /// AI suspicion score (0-100)
    pub suspicion_score: u8,

    /// Cooldown until timestamp (if throttled)
    pub cooldown_until: i64,
}

pub fn check_fast_lane_eligibility(
    tracker: &FastLaneTracker,
    current_time: i64,
) -> FastLaneEligibility {
    // Cooldown check
    if tracker.cooldown_until > current_time {
        return FastLaneEligibility::Throttled { until: tracker.cooldown_until };
    }

    // Frequency check (max 5 fast-lane claims per 30 days)
    if tracker.claims_30d >= 5 {
        return FastLaneEligibility::LimitReached;
    }

    // Amount check (max $2,000 fast-lane per 30 days)
    if tracker.amount_30d >= 200_000_000_000 {
        return FastLaneEligibility::AmountLimitReached;
    }

    // AI suspicion check
    if tracker.suspicion_score > 75 {
        return FastLaneEligibility::RequiresReview;
    }

    FastLaneEligibility::Eligible
}
```

### 5.3 Cohort Analysis

Monitor for adverse selection patterns:

```rust
pub struct CohortMetrics {
    /// Cohort identifier (enrollment period)
    pub cohort_id: u32,

    /// Number of members in cohort
    pub member_count: u32,

    /// Average claims per member
    pub avg_claims_per_member: u64,

    /// Loss ratio for this cohort
    pub loss_ratio_bps: u16,

    /// AI-predicted future loss ratio
    pub predicted_loss_ratio: u16,

    /// Adverse selection risk score (0-100)
    pub adverse_selection_score: u8,

    /// Flags
    pub flags: CohortFlags,
}
```

**Flags**:
- `HIGH_UTILIZATION`: Claims significantly above expected
- `ADVERSE_SELECTION_RISK`: Pattern suggests adverse selection
- `RAPID_ENROLLMENT`: Unusual enrollment spike
- `DISENROLLMENT_SPIKE`: Members leaving after claims

---

## 6. Price Validation

### 6.1 UCR Database

Usual, Customary, and Reasonable (UCR) pricing with AI enhancement:

```rust
pub struct UcrPriceEntry {
    /// CPT/HCPCS procedure code
    pub procedure_code: [u8; 8],

    /// Geographic region code
    pub region_code: u16,

    /// Price percentiles (in USDC cents)
    pub p25_price: u64,
    pub p50_price: u64,
    pub p75_price: u64,
    pub p90_price: u64,

    /// AI-predicted fair price for this region
    pub ai_fair_price: u64,

    /// Confidence in AI price
    pub ai_confidence: u16,

    /// Last update timestamp
    pub last_updated: i64,

    /// Data source count (for credibility)
    pub sample_count: u32,
}
```

### 6.2 Price Validation Flow

```rust
pub fn validate_claim_price(
    claim_amount: u64,
    ucr: &UcrPriceEntry,
) -> PriceValidation {
    if claim_amount <= ucr.p75_price {
        PriceValidation::Approved
    } else if claim_amount <= ucr.p90_price {
        PriceValidation::RequiresReview {
            reason: "Above 75th percentile"
        }
    } else {
        PriceValidation::Flagged {
            reason: "Above 90th percentile",
            ucr_p90: ucr.p90_price,
            claimed: claim_amount,
        }
    }
}
```

---

## 7. Oracle Architecture

### 7.1 AI Oracle Integration

The on-chain contracts integrate with off-chain AI services:

```rust
pub struct AiOracleConfig {
    /// Oracle authority (can submit AI decisions)
    pub oracle_authority: Pubkey,

    /// Backup oracle (if primary fails)
    pub backup_oracle: Pubkey,

    /// Maximum staleness for AI decisions (seconds)
    pub max_decision_age: i64,

    /// Auto-approve threshold score (0-100)
    pub auto_approve_threshold: u8,

    /// Escalation threshold score (0-100)
    pub escalation_threshold: u8,

    /// Is AI processing enabled
    pub is_enabled: bool,
}
```

### 7.2 Decision Recording

```rust
pub struct AiDecisionRecord {
    /// Claim this decision relates to
    pub claim_id: Pubkey,

    /// Model version that produced this decision
    pub model_version: [u8; 32],

    /// Decision confidence (basis points)
    pub confidence_score: u16,

    /// Fraud probability score (0-10000 bps)
    pub fraud_score: u16,

    /// Recommended action
    pub recommendation: AiRecommendation,

    /// Timestamp of inference
    pub inference_timestamp: i64,

    /// Hash of input features (for reproducibility)
    pub feature_hash: [u8; 32],

    /// Oracle authority that submitted this decision
    pub oracle_authority: Pubkey,
}

pub enum AiRecommendation {
    AutoApprove,
    ApproveWithReview,
    RequiresCommittee,
    Deny { reason_code: u16 },
    FraudAlert,
}
```

### 7.3 Oracle Security

| Mechanism | Purpose |
|-----------|---------|
| Multiple providers | Redundancy |
| Stake-weighted consensus | Quality assurance |
| Slashing | Incorrect/malicious decisions |
| Rate limiting | Prevent spam |
| Decision verification | Reproducibility |

---

## 8. Model Governance

### 8.1 Model Registry

All AI models in production are registered on-chain:

```rust
pub struct ModelRegistry {
    /// Model unique identifier
    pub model_id: [u8; 32],

    /// Model version (semantic versioning)
    pub version: u32,

    /// Model type
    pub model_type: ModelType,

    /// IPFS hash of model artifacts
    pub artifact_hash: [u8; 32],

    /// Training data hash (reproducibility)
    pub training_data_hash: [u8; 32],

    /// Performance metrics
    pub accuracy: u16,
    pub precision: u16,
    pub recall: u16,
    pub f1_score: u16,

    /// Approval status
    pub approved_by: Pubkey,
    pub approved_at: i64,

    /// Active status
    pub is_active: bool,
}
```

### 8.2 Model Update Process

```
1. PROPOSAL
   Data science team proposes new model version
                    ↓
2. VALIDATION
   Independent validation on held-out test set
                    ↓
3. SHADOW MODE
   Run alongside production for 2 weeks
                    ↓
4. COMMITTEE REVIEW
   Actuarial committee reviews performance
                    ↓
5. DAO VOTE
   Community approves model deployment
                    ↓
6. GRADUAL ROLLOUT
   10% → 50% → 100% traffic
```

---

## 9. Privacy & Security

### 9.1 HIPAA Compliance

| Data Type | Location | Protection |
|-----------|----------|------------|
| PHI | Off-chain only | Encrypted at rest |
| Financial | On-chain | Pseudonymized |
| Model inputs | Off-chain | Anonymized features |
| Decisions | On-chain | Hashed references |

### 9.2 Privacy Techniques

- **No PHI on public blockchain**
- **Federated learning** for model updates
- **Differential privacy** for aggregate statistics
- **Zero-knowledge proofs** for eligibility (future)

### 9.3 Model Security

| Threat | Mitigation |
|--------|------------|
| Adversarial attacks | Robustness testing |
| Model drift | Continuous monitoring |
| Data poisoning | Training data validation |
| Model extraction | Rate limiting, watermarking |

---

## 10. Future Roadmap

### Phase 2 Enhancements

| Feature | Description |
|---------|-------------|
| NLP for documents | Automated claim document analysis |
| Computer vision | Medical bill OCR |
| Personalized pricing | Risk-adjusted premiums |
| Predictive health | Opt-in health analytics |

### Phase 3 Enhancements

| Feature | Description |
|---------|-------------|
| Federated learning | Cross-network model training |
| On-chain inference | As Solana compute improves |
| Cross-chain oracles | Multi-blockchain data |
| Real-time streaming | Continuous model updates |

---

## Performance Targets

| Metric | Target | Notes |
|--------|--------|-------|
| Fast-lane auto-approval rate | >80% | Of eligible claims |
| Fraud detection precision | >95% | True positives |
| Fraud detection recall | >90% | Caught frauds |
| Claims processing (fast-lane) | <100ms | End-to-end |
| Claims processing (AI review) | <24 hours | With notification |
| False positive rate (fraud) | <2% | To minimize friction |
| Model inference latency | <50ms | Per decision |

---

<p align="center">
  <strong>AI-powered efficiency. Human oversight. On-chain transparency.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*  
*Status: PUBLISHED*

---

## References

1. Chen, T. & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System
2. Liu, F., Ting, K.M. & Zhou, Z.H. (2008). Isolation Forest for Anomaly Detection
3. Apollo Care Protocol Actuarial Specification
4. Solana Program Library Documentation
5. Morrisey, M.A. (2020). Health Insurance, Third Edition
