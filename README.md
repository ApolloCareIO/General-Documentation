> Forward‑Looking Statement: This document contains forward‑looking statements subject to significant risks and uncertainties. Nothing herein is investment, legal, or medical advice. Features, timelines, and parameters are examples and remain subject to DAO approval and market/regulatory conditions.

# Apollo Care Documentation Repository

Apollo Care is a **community‑owned health coverage protocol** built on Solana.  It aims to provide transparent, cost‑sharing health coverage, not traditional insurance.  Individuals secure coverage by contributing monthly USDC premiums into a shared pool; ownership of the $APH token is **optional** and confers governance rights and the ability to participate in staking/backstop programmes【14317910318221†L97-L110】【14317910318221†L136-L140】.

**Token Address (Solana):** `6S3T6f1mmhxQWKR1gMiZR1SZLpu396jnnRMGqAZUj3Qj`  
**Presale link:** (Presale link to be added when live)

## Overview

Apollo Care separates health coverage from token ownership. Members obtain coverage by choosing a coverage level and paying monthly USDC premiums; they do not need to own any tokens to access care【14317910318221†L97-L110】. $APH holders participate in governance and may optionally stake tokens as backstop capital【684450145845687†L180-L207】.

### Member Journey

1. **Enrollment in Coverage** – Members select a coverage level and pay monthly USDC contributions into the community pool【14317910318221†L110-L113】.  
2. **Claims Submission** – AI‑powered document processing extracts data from medical bills; simple claims are auto‑approved within minutes【14317910318221†L115-L118】.  
3. **Automated Review** – Routine claims are evaluated automatically; valid claims trigger immediate payment【14317910318221†L119-L123】.  
4. **Payment** – Smart contracts disburse funds from the Premium & Capital Pool directly to member wallets or providers【14317910318221†L124-L128】.

### Capital & Liquidity Structure

Apollo maintains a three‑tier capital model to ensure solvency and fairness:

* **Tier 0 – Real‑Time Liquidity:** immediate liquidity for daily claims (0–30 days)【14317910318221†L354-L361】.  
* **Tier 1 – Operating Reserve:** a buffer (1–2 months of claims) funded by excess contributions and reinsurance【14317910318221†L354-L361】.  
* **Tier 2 – Contingent Capital:** long‑term protection (6+ months) sourced from the DAO Treasury and capped, staked $APH【14317910318221†L354-L370】.

A flow‑of‑funds illustration of the claims payment waterfall is provided in `docs/claims-liquidity-waterfall.md`.

### Governance

Apollo operates under a DAO model where $APH holders vote on proposals, elect committees, and adjust protocol parameters.  The platform is legally wrapped as a DAO LLC【830535318348417†L50-L67】.  Coverage members are beneficiaries of the cost‑sharing program, whereas $APH token holders own and govern the protocol【830535318348417†L69-L73】.  Committee structures and voting mechanics are detailed in `governance/overview.md`.

## Repository Contents

* `docs/` – technical papers, specifications, tokenomics, architecture, actuarial models, operations and liquidity waterfall diagrams.  
* `governance/` – governance overview and committee descriptions.  
* `legal/` – regulatory notice and phase description.  
* `SECURITY.md`, `RISK.md`, `ROADMAP.md` – guidelines on security, risks and phased roadmap.  
* `.github/` – community issue and pull request templates.

For in‑depth reading, see the [Whitepaper](docs/whitepaper.md) and the [Actuarial Specification](docs/actuarial-spec.md).

### Release Notes

* **v0.1.0 (pre‑ICO docs)** – initial public documentation release.  Includes whitepaper, tokenomics, actuarial and operations specifications, governance overview, legal phase notice, security guidelines, risk disclosures and roadmap.

> Forward‑Looking Statement: This document contains forward‑looking statements subject to significant risks and uncertainties. Nothing herein is investment, legal, or medical advice. Features, timelines, and parameters are examples and remain subject to DAO approval and market/regulatory conditions.