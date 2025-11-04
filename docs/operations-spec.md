> Forward‑Looking Statement: This document contains forward‑looking statements subject to significant risks and uncertainties. Nothing herein is investment, legal, or medical advice. Features, timelines, and parameters are examples and remain subject to DAO approval and market/regulatory conditions.

# Operations & Business Design (Public Summary)

This specification outlines Apollo Care’s operational model and business processes.  It provides a public‑facing overview derived from the internal operations specification without exposing proprietary logic or personal data.

## Legal Wrapper & Cost‑Sharing Status

Apollo operates through **Apollo Protocol LLC**, a Wyoming DAO LLC【830535318348417†L50-L67】.  This structure provides legal recognition while allowing governance to occur on‑chain.  Members participate in a **voluntary cost‑sharing program**, not an insurance contract【830535318348417†L88-L100】.  Membership terms emphasise that Apollo pays valid claims on a best‑efforts basis but cannot guarantee payment in the legal sense; nevertheless, the protocol maintains reserves and risk controls comparable to insurers to build trust【830535318348417†L88-L100】.

## Onboarding & Premiums

### Member Enrollment

Prospective members join by selecting a coverage plan and paying monthly **USDC contributions** into the community pool【14317910318221†L97-L113】.  Enrollment is open continuously but may be throttled if reserves fall below safe thresholds to protect solvency【214961381664349†L1575-L1584】.  A simple onboarding flow collects demographic and health data, issues a non‑transferable coverage NFT and sets up recurring contributions via smart contract or off‑chain payment processor.

### Contribution Handling

Monthly contributions function similarly to premiums: they fund claims and reserves.  The smart contract separates incoming funds into the Tier 0 liquidity buffer, Tier 1 reserve and contingency allocations according to preset ratios.  Contributions are recorded on‑chain for transparency; members can see their payment history and coverage status at any time.

## Claims Processing Workflow

Members submit claims through Apollo’s mobile/web interface by uploading bills or selecting provider invoices.  The claims engine follows the three‑lane process described in the actuarial specification (fast‑lane auto‑approval, AI‑assisted triage and committee review)【214961381664349†L745-L899】.  Approved claims are paid from the liquidity buffer or reserves, with no out‑of‑network penalties – Apollo strives for broad provider choice【14317910318221†L215-L224】.

### Oracle & Data Sources

Apollo uses multiple oracles to verify pricing and fraud patterns: reference price databases, regional cost indices and third‑party claim histories.  AI models (trained off‑chain) extract data from documents and flag anomalies.  Only minimal, de‑identified data is stored on‑chain to protect member privacy.

### Committee Roles

* **Claims Committee:** elected by $APH holders; reviews escalated claims and handles appeals.  Members must recuse themselves in cases of conflict.
* **Risk/Actuarial Committee:** sets contribution parameters, monitors loss ratios, adjusts ShockFactor and enrolment rules and recommends capital calls.
* **Treasury Committee:** manages reserves, oversees investment of surplus USDC into low‑risk yields, coordinates reinsurance purchases and executes Tier 2 transfers.
* **Growth Committee:** focuses on member recruitment, partnerships and communications.

Committees operate under delegated authority with limits.  Actions beyond defined thresholds (e.g., large rate changes or reserve drawdowns) require a DAO vote.

## Safeguards & Transparency

* **Enrollment Throttling:** If capital adequacy or reserves fall below safe levels, the Actuarial Committee may temporarily pause or limit new memberships【214961381664349†L1575-L1584】.
* **Emergency Claims Protocol:** In rare scenarios where Tier 1 and Tier 2 are depleted, non‑urgent claims may be deferred or partially paid, with full DAO oversight【214961381664349†L1586-L1603】.
* **Real‑Time Reporting:** The protocol publishes reserve levels, claim payouts and key metrics on‑chain or via dashboards【214961381664349†L1655-L1668】.  Members can track whether the program is meeting capital targets and propose adjustments.

## Provider & Member Experience

Apollo negotiates reference‑based pricing with providers and aims to offer near‑real‑time settlement.  Members pay providers out‑of‑pocket for small services and are instantly reimbursed, or providers can bill Apollo directly via crypto‑to‑fiat gateways.  There is no distinction between “in‑network” and “out‑of‑network”; coverage is portable and transparent【14317910318221†L215-L224】.

## Phased Implementation

Apollo’s operations unfold in phases:

1. **Phase 1 – Cost‑Sharing Ministry Launch:** Apollo operates as a health care sharing ministry, emphasising community cost sharing and voluntary contributions【830535318348417†L117-L130】.  Reserves and risk controls mirror those of insurers, but there is no formal insurance license.
2. **Phase 2 – Hybrid & Sandbox:** Apollo pursues limited insurance licensing or partnerships while maintaining the cost‑sharing model【830535318348417†L180-L198】.  Compliance functions and regulatory reporting are added, and a regulated insurance option may be offered in parallel.
3. **Phase 3 – Full Regulatory Pathway:** Subject to DAO approval and market conditions, Apollo aims to operate as a fully regulated insurer, integrating its DAO governance with statutory requirements.  Capital reserves, reinsurance and compliance will evolve accordingly.

Each phase is executed with community approval and regulatory guidance.  Features and timelines described here are aspirational and may evolve.

> Forward‑Looking Statement: This document contains forward‑looking statements subject to significant risks and uncertainties. Nothing herein is investment, legal, or medical advice. Features, timelines, and parameters are examples and remain subject to DAO approval and market/regulatory conditions.