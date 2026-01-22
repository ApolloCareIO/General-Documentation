# Apollo Care Glossary

<p align="center">
  <strong>Key Terms and Definitions</strong><br/>
  <em>Version 2.0 | January 2026</em>
</p>

---

## A

### ACA (Affordable Care Act)
U.S. federal statute enacted in 2010 that reformed healthcare insurance, requiring minimum coverage standards, prohibiting discrimination based on health status, and mandating minimum Medical Loss Ratios.

### Age Rating
The practice of adjusting insurance premiums based on the age of the insured. Under ACA rules, the maximum ratio allowed is 3:1 (oldest adults can be charged at most 3x what youngest adults pay).

### APH (Apollo Care Token)
The native governance and utility token of Apollo Care Protocol. Used for voting, staking, and community participation. Not required for health coverage.

### Adverse Selection
The tendency for individuals with higher expected healthcare costs to be more likely to purchase coverage, potentially destabilizing the risk pool.

---

## B

### Buyback & Burn
A mechanism where Apollo uses surplus USDC to purchase APH tokens on the open market and permanently destroy them, reducing circulating supply and potentially increasing per-token value.

---

## C

### CAR (Capital Adequacy Ratio)
Apollo's primary solvency metric, calculated as (USDC Reserves + Eligible Staked APH Value) / Expected Annual Claims. Expressed as a percentage (125% = 1.25x coverage).

### Claims Committee
An elected group of APH token holders with healthcare expertise responsible for reviewing complex or large claims that exceed automated processing thresholds.

### CMS (Centers for Medicare & Medicaid Services)
U.S. federal agency that administers Medicare, Medicaid, and the ACA marketplace. Sets standards for health insurance rating and compliance.

### Cohort
A group of members who enrolled during the same time period, tracked separately for loss ratio analysis and adverse selection monitoring.

---

## D

### DAO (Decentralized Autonomous Organization)
An organization represented by rules encoded as smart contracts, controlled by organization members rather than a central authority. Apollo is governed as a DAO.

### DEX (Decentralized Exchange)
A cryptocurrency exchange that operates without a central authority, allowing peer-to-peer trading. APH is traded on DEXs like Raydium.

### Development Factor
In IBNR calculation, a multiplier (typically 1.15 or 15%) applied to account for claims that may develop beyond initial estimates.

---

## F

### Fast-Lane
Apollo's Tier 1 claims processing for small, routine claims (<$500-$1,000) that are automatically approved and paid within seconds without human review.

### Fraud Flag
An indicator triggered by Apollo's AI system suggesting potential fraudulent activity in a claim submission.

---

## G

### Governance
The system of rules, practices, and processes by which Apollo Care is directed and controlled. Token holders participate in governance through proposals and voting.

### Green Zone
The healthiest CAR status (≥150%), indicating strong solvency with unlimited enrollment and normal operations.

---

## H

### HCSM (Healthcare Sharing Ministry)
A healthcare cost-sharing arrangement where members voluntarily share medical expenses. Not insurance, and exempt from ACA requirements. Apollo's Phase 1 structure.

### HIPAA (Health Insurance Portability and Accountability Act)
U.S. law that protects patient health information privacy and sets security standards for healthcare data.

---

## I

### IBNR (Incurred But Not Reported)
Reserve for claims that have been incurred (medical services rendered) but not yet submitted for payment. Calculated as Average Daily Claims × Reporting Lag × Development Factor.

### ICHRA (Individual Coverage Health Reimbursement Arrangement)
An employer-funded arrangement allowing companies to reimburse employees for individual health insurance on a tax-free basis.

---

## L

### Loading
The portion of insurance premiums that goes to expenses other than claims (administration, reserves, profit). Apollo targets ≤10% loading for 90%+ MLR.

### Loss Ratio
The ratio of claims paid to premiums collected. Similar to MLR but may exclude quality improvement expenses.

---

## M

### MLR (Medical Loss Ratio)
The percentage of premium dollars spent on medical claims and quality improvement. ACA requires minimum 80-85%; Apollo targets 90%+.

### Multisig
A wallet or contract requiring multiple signatures to execute transactions. Used for treasury management and emergency actions.

---

## O

### Orange Zone
CAR status between 100-124%, indicating financial stress. Enrollment limited to 100/month, distributions paused, ShockFactor up to 1.5x permitted.

### Oracle
A service that provides external data to smart contracts. Apollo uses AI oracles to submit claims decisions on-chain.

---

## P

### Phase 1/2/3
Apollo's three-stage regulatory pathway from Healthcare Sharing Ministry to Regulatory Pilot to Licensed Insurance Carrier.

### Premium
The amount paid for health coverage. In Apollo, premiums are paid in USDC stablecoins.

### Pure Premium
The expected cost of claims per insured, before adding loading for expenses.

---

## Q

### Quorum
The minimum participation level required for a governance vote to be valid. Varies by proposal type (10-25% of token supply).

---

## R

### R-MCA (Risk-Managed Contribution Algorithm)
Apollo's CMS-compliant pricing methodology that calculates premiums based on age, tobacco use, location, and pool risk factors.

### Red Zone
CAR status below 100%, indicating emergency conditions. Enrollment frozen, ShockFactor up to 2.0x with DAO approval required.

### Reinsurance
Insurance purchased by an insurer to transfer risk. Apollo uses layered reinsurance (specific, aggregate, catastrophic) in later phases.

---

## S

### ShockFactor
A multiplier applied to base premiums during stress periods to increase revenue and rebuild reserves. Ranges from 1.0x (normal) to 2.0x (emergency).

### Slashing
The penalty mechanism where stakers lose a portion of their staked tokens due to protocol insolvency or, in some systems, malicious behavior.

### Staking
Locking APH tokens in the protocol to provide capital backing and earn yields. Three tiers: Conservative, Standard, Aggressive.

### Stop-Loss
A type of reinsurance that protects against individual claims exceeding a threshold (specific stop-loss) or aggregate claims exceeding a percentage of expected (aggregate stop-loss).

---

## T

### Tier 0/1/2
Apollo's three-tier reserve structure: Liquidity Buffer (Tier 0), Operating Reserve (Tier 1), and Contingent Capital (Tier 2).

### Timelock
A delay between when a governance proposal passes and when it executes, allowing for review and emergency intervention if needed.

### Token-2022
Solana's enhanced token program supporting extensions like transfer fees, metadata, and interest-bearing tokens. APH uses Token-2022.

### Transfer Fee
A 2% fee applied to APH token transfers (post-presale) that funds protocol sustainability.

### TWAP (Time-Weighted Average Price)
A pricing mechanism that executes trades over a period to minimize market impact. Used for APH liquidations.

---

## U

### UCR (Usual, Customary, and Reasonable)
A database of typical prices for medical procedures by region, used to validate claim amounts.

### USDC
A stablecoin pegged 1:1 to the US dollar, issued by Circle. Apollo uses USDC for premiums, reserves, and claim payments.

---

## W

### Waterfall
The priority order in which reserve tiers are tapped to pay claims: Tier 0 → Tier 1 → Tier 2 USDC → Staked APH → Insurance Reserve.

### Wyoming DAO LLC
A legal structure under Wyoming law (W.S. 17-31-101) that provides limited liability and legal recognition to DAOs. Apollo Protocol DAO LLC uses this structure.

---

## Y

### Yellow Zone
CAR status between 125-149%, indicating caution. Enrollment throttled to 500/month, ShockFactor up to 1.2x with committee approval.

### Yield
The return earned by stakers for providing capital to backstop the insurance pool. Ranges from 3-15% APY depending on tier.

---

<p align="center">
  <strong>Questions? Ask in our community channels.</strong>
</p>

---

*Document Version: 2.0*  
*Last Updated: January 2026*
