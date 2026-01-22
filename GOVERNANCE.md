# Apollo Care Governance

<p align="center">
  <strong>DAO Structure, Voting, and Committee Organization</strong><br/>
  <em>Version 2.0 | January 2026</em>
</p>

---

## Table of Contents

1. [Overview](#1-overview)
2. [The Apollo DAO](#2-the-apollo-dao)
3. [Governance Process](#3-governance-process)
4. [Committees](#4-committees)
5. [Voting Mechanics](#5-voting-mechanics)
6. [Emergency Procedures](#6-emergency-procedures)
7. [Legal Structure](#7-legal-structure)

---

## 1. Overview

### 1.1 Governance Philosophy

Apollo Care is governed by its community through a decentralized autonomous organization (DAO). The governance model ensures:

- **Democratic Control**: Token holders vote on major decisions
- **Expert Execution**: Specialized committees handle day-to-day operations
- **Transparency**: All decisions recorded on-chain
- **Accountability**: Committees answerable to the DAO

### 1.2 Key Principle

> Healthcare coverage is purchased through monthly USDC contributions. $APH token ownership provides governance rights but is **not required** for health coverage.

---

## 2. The Apollo DAO

### 2.1 Membership

All $APH token holders collectively form the Apollo DAO—the ultimate authority over the protocol.

| Attribute | Description |
|-----------|-------------|
| **Voting Power** | 1 APH = 1 vote |
| **Governance Rights** | Vote on proposals, elect committees |
| **Proposal Rights** | Minimum threshold required |
| **No Token Required** | For coverage (only for governance) |

### 2.2 DAO Authority

The DAO has power over all major aspects:

| Domain | Examples |
|--------|----------|
| **Coverage Policies** | What's covered, exclusions, limits |
| **Contribution Rates** | Premium adjustments, ShockFactor |
| **Treasury Management** | Reserve allocation, surplus use |
| **Protocol Upgrades** | Smart contract updates |
| **Committee Elections** | Appoint/remove committee members |
| **Phase Transitions** | Regulatory pathway decisions |

### 2.3 What the DAO Does NOT Control

- Individual claim decisions (committee authority)
- Day-to-day operational decisions (delegated)
- Smart contract security patches (emergency authority)

---

## 3. Governance Process

### 3.1 Proposal Lifecycle

```
┌─────────────────────────────────────────────────────────────────┐
│                      PROPOSAL LIFECYCLE                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. SUBMISSION                                                  │
│     └─ Any holder with minimum threshold submits proposal       │
│        (e.g., 1% of supply or 10M APH)                          │
│                           │                                     │
│                           ▼                                     │
│  2. DISCUSSION (7 days)                                         │
│     └─ Posted on Apollo Agora (forum)                           │
│     └─ Community debate and refinement                          │
│     └─ Non-binding temperature check                            │
│                           │                                     │
│                           ▼                                     │
│  3. FORMAL SUBMISSION                                           │
│     └─ Proposal submitted on-chain                              │
│     └─ Snapshot of token holdings                               │
│                           │                                     │
│                           ▼                                     │
│  4. VOTING (3 days)                                             │
│     └─ Token holders cast votes                                 │
│     └─ Vote weight = token holdings                             │
│     └─ Delegation allowed                                       │
│                           │                                     │
│                           ▼                                     │
│  5. TIMELOCK (1-2 days)                                         │
│     └─ Review period after passing                              │
│     └─ Emergency veto possible (guardian)                       │
│                           │                                     │
│                           ▼                                     │
│  6. EXECUTION                                                   │
│     └─ Automatic execution by smart contract                    │
│     └─ Or committee action for off-chain items                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 Proposal Types

| Type | Examples | Quorum | Approval |
|------|----------|--------|----------|
| **Standard** | Fee adjustments, minor parameters | 10% | >50% |
| **Significant** | Coverage changes, committee elections | 15% | 60% |
| **Critical** | Protocol upgrades, phase transitions | 20% | 67% |
| **Constitutional** | Governance rules, fundamental changes | 25% | 75% |
| **Emergency** | Security fixes, urgent actions | 5% | 67% |

### 3.3 Delegation

Token holders can delegate voting power:
- Delegate to any address
- Retain right to override on specific votes
- Delegation can be revoked anytime
- Common for passive holders to delegate to active participants

---

## 4. Committees

### 4.1 Committee Structure

The DAO charters specialized committees for efficient operations:

```
                       ┌─────────────────┐
                       │   APOLLO DAO    │
                       │ (All APH Holders)│
                       └────────┬────────┘
                                │
           ┌────────────────────┼────────────────────┐
           │                    │                    │
           ▼                    ▼                    ▼
    ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
    │   CLAIMS    │     │    RISK &   │     │  TREASURY   │
    │  COMMITTEE  │     │  ACTUARIAL  │     │  COMMITTEE  │
    └─────────────┘     └─────────────┘     └─────────────┘
           │                    │                    │
           │                    │                    │
           ▼                    ▼                    ▼
    ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
    │   GROWTH    │     │  TECHNICAL  │     │  EMERGENCY  │
    │ PARTNERSHIP │     │  COMMITTEE  │     │  GUARDIANS  │
    └─────────────┘     └─────────────┘     └─────────────┘
```

### 4.2 Committee Descriptions

#### Claims Committee

| Attribute | Details |
|-----------|---------|
| **Purpose** | Review complex/large claims |
| **Size** | 5-7 members |
| **Qualifications** | Healthcare, legal, or actuarial expertise |
| **Authority** | Approve/deny claims within limits |
| **Limitations** | Cannot set policy; DAO appeal available |

#### Risk & Actuarial Committee

| Attribute | Details |
|-----------|---------|
| **Purpose** | Monitor pool health, recommend rate adjustments |
| **Size** | 3-5 members |
| **Qualifications** | Actuarial, finance, or data science background |
| **Authority** | Adjust parameters within ±5% |
| **Limitations** | Larger changes require DAO vote |

#### Treasury Committee

| Attribute | Details |
|-----------|---------|
| **Purpose** | Manage financial assets, oversee reserves |
| **Size** | 3-5 members |
| **Qualifications** | Finance, treasury management experience |
| **Authority** | Allocate within approved budget |
| **Limitations** | Major moves require DAO approval |

#### Growth & Partnership Committee

| Attribute | Details |
|-----------|---------|
| **Purpose** | Marketing, member acquisition, partnerships |
| **Size** | 3-5 members |
| **Qualifications** | Marketing, business development |
| **Authority** | Spend from growth fund |
| **Limitations** | Within quarterly budget |

#### Technical Committee

| Attribute | Details |
|-----------|---------|
| **Purpose** | Smart contract maintenance, upgrades |
| **Size** | 3-5 members |
| **Qualifications** | Blockchain development expertise |
| **Authority** | Bug fixes, minor upgrades |
| **Limitations** | Major changes require DAO vote |

#### Emergency Guardians

| Attribute | Details |
|-----------|---------|
| **Purpose** | Rapid response to security threats |
| **Size** | 3 members (2-of-3 multisig) |
| **Qualifications** | Security expertise, trusted community members |
| **Authority** | Pause contracts, emergency actions |
| **Limitations** | Actions reviewed by DAO within 48 hours |

### 4.3 Committee Accountability

| Mechanism | Description |
|-----------|-------------|
| **Regular Reports** | Monthly/quarterly updates to DAO |
| **DAO Override** | Any committee decision can be appealed |
| **Elections** | Regular elections (typically annual) |
| **Removal** | DAO can remove members at any time |
| **Transparency** | All committee actions logged on-chain |

---

## 5. Voting Mechanics

### 5.1 On-Chain Voting

```rust
pub struct Proposal {
    /// Unique proposal ID
    pub id: u64,

    /// Proposer address
    pub proposer: Pubkey,

    /// Proposal type (determines thresholds)
    pub proposal_type: ProposalType,

    /// Description hash (IPFS)
    pub description_hash: [u8; 32],

    /// Start timestamp
    pub voting_starts: i64,

    /// End timestamp
    pub voting_ends: i64,

    /// Votes for
    pub votes_for: u64,

    /// Votes against
    pub votes_against: u64,

    /// Votes abstain
    pub votes_abstain: u64,

    /// Status
    pub status: ProposalStatus,

    /// Execution timelock end
    pub timelock_end: i64,
}
```

### 5.2 Vote Calculation

```
Voting Power = Token Balance + Delegated Tokens - Delegated Away
```

### 5.3 Quorum Requirements

| Proposal Type | Quorum (% of Supply) |
|---------------|---------------------|
| Standard | 10% |
| Significant | 15% |
| Critical | 20% |
| Constitutional | 25% |
| Emergency | 5% |

**Example**: For a Standard proposal with 1B total supply, at least 100M APH must vote.

### 5.4 Approval Thresholds

```
Approval Rate = Votes For / (Votes For + Votes Against)
```

*Abstentions count for quorum but not approval calculation.*

---

## 6. Emergency Procedures

### 6.1 Emergency Types

| Type | Examples | Response |
|------|----------|----------|
| **Security** | Exploit discovered | Guardian pause |
| **Solvency** | CAR drops below 100% | Committee action |
| **Operational** | Oracle failure | Technical intervention |
| **Market** | Extreme APH volatility | Circuit breakers |

### 6.2 Emergency Response Flow

```
EMERGENCY DETECTED
        │
        ▼
┌───────────────────┐
│ GUARDIAN ACTION   │ ← Immediate (minutes)
│ • Pause contracts │
│ • Freeze assets   │
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│ COMMITTEE REVIEW  │ ← Short-term (hours)
│ • Assess damage   │
│ • Propose fix     │
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│ DAO RATIFICATION  │ ← Medium-term (24-48 hours)
│ • Emergency vote  │
│ • Approve actions │
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│ NORMAL OPERATIONS │ ← Resolution
│ • Resume services │
│ • Post-mortem     │
└───────────────────┘
```

### 6.3 Governance Alerts

Smart contracts emit alerts for:
- CAR dropping below thresholds
- Large claims submitted
- Unusual activity patterns
- Reserve drawdowns

These alerts can automatically trigger DAO discussions or emergency votes.

---

## 7. Legal Structure

### 7.1 Wyoming DAO LLC

**Apollo Protocol DAO LLC** is registered in Wyoming under W.S. 17-31-101 et seq.

| Benefit | Description |
|---------|-------------|
| **Legal Recognition** | Smart contract governance legally recognized |
| **Limited Liability** | Members and token holders protected |
| **Contractual Capacity** | Can enter contracts, hire providers |
| **Asset Holding** | Can own property and assets |
| **Regulatory Pathway** | Foundation for insurance licensing |

### 7.2 Member vs. Token Holder

| Attribute | Coverage Member | APH Token Holder |
|-----------|-----------------|------------------|
| **Relationship** | Policyholder | Governance participant |
| **Rights** | Coverage benefits | Voting rights |
| **Obligations** | Pay premiums | None (voluntary staking) |
| **Liability** | None | None (LLC protection) |

### 7.3 Governance-Legal Bridge

| On-Chain Action | Legal Effect |
|-----------------|--------------|
| Proposal passes | Binding resolution of the LLC |
| Committee elected | Officers of the LLC |
| Treasury transfer | Authorized expenditure |
| Protocol upgrade | Amendment to operating agreement |

---

## Summary

Apollo Care governance provides:

| Feature | Benefit |
|---------|---------|
| **Token Voting** | Democratic control |
| **Committee System** | Expert execution |
| **On-Chain Records** | Transparency |
| **Legal Structure** | Compliance and protection |
| **Emergency Procedures** | Security and resilience |

---

<p align="center">
  <strong>Governed by the community. For the community.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*  
*Status: PUBLISHED*
