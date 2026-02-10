---
yip: 88
title: Governance Overhaul: DAO Restructuring
author: 0xPickles and the governance team contributors
discussions-to: https://gov.yearn.fi/t/yip-xx-governance-overhaul-dao-restructuring/14553
status: Proposed
created: 2025-09-28
---

## Simple Summary
This proposal outlines the operational and financial restructuring of the Yearn DAO to focus all efforts on revenue generation and on-chain accountability.

**IMPORTANT NOTE:** This proposal is the first of three interconnected parts of a single initiative designed to overhaul Yearn's operations, tokenomics, and contributor incentives.

- **Part I: Operations & DAO Restructuring (This Proposal)**
- [Part II: stYFI Tokenomics & Migration](https://gov.yearn.fi/t/yip-88-governance-overhaul-styfi/)
- [Part III: Contributor & Team Incentives](https://gov.yearn.fi/t/yip-88-governance-overhaul-incentives/)

All three parts will be discussed in parallel on the forum but will be voted on as a single, all-or-nothing package in one Snapshot vote for **YIP-XX**. If the unified proposal passes, all three parts will be implemented. If it fails, none will be.


## Abstract
**If the complete YIP-XX initiative is adopted**, this part of the proposal will:
- Reorganize Yearn contributors around revenue-earning teams, except for a minimal DAO operations team.
- Require all teams to use on-chain revenue splitters for transparent accounting.
- Mandate on-chain financial reporting to justify all future budget requests.

## Motivation
The primary driver for this proposal is to reorient the entire Yearn DAO towards sustainable **growth and operational excellence**. The idea is to create a transparent and accountable framework that directly supports the value accrual mechanisms detailed in Part II and justifies the incentive structures in Part III.

The motivation for this specific operational model is rooted in several key principles:
*   **Center the org around autonomous, revenue-generating units:** The fundamental principle of this reorg is that teams should be structured as self-sufficient units focused on generating revenue. Each team should encompass all critical functions (e.g., development, strategy, marketing) needed to operate its products. This "full-circle" structure is essential for enabling clear Profit & Loss (P&L) attribution, allowing the DAO to accurately track all earnings and costs associated with each team.
*   **Move accountability on-chain:** Moving from off-chain tracking and manual reporting to on-chain revenue splitters and automated tracking provides unimpeachable, data in real-time. This empowers the DAO to make objective, data-driven decisions about resource allocation, ensuring that we fund what works and that every team's contribution to the bottom line is clear.
*   **Maintain a lean and accountable support system:** Certain core functions are necessary for the DAO to operate. By defining a minimal, well-scoped DAO Operations (DAO-ops) team, we ensure this essential back-office work is supported. Crucially, this team remains fully accountable to the DAO, which can regularly review and justify its scope and budget, preventing operational bloat.
*   **Establish guidelines:** The transition to this new operational model will have complexities. This YIP intentionally avoids micromanaging that process. Instead, it establishes the foundational ground rules and clear end-state goals, empowering the teams themselves to collaborate and forge the most effective paths to implementation.

### 4.1 Alternatives Considered

In developing this proposal, we evaluated several alternative paths for restructuring the DAO. These were considered and rejected for the following reasons:
*   **Merge into a single "Mono-Team":** We considered dissolving all yTeams and consolidating contributors into a single, hierarchical organization. This was rejected as it introduces significant centralization vectors, creates single points of failure in management, and runs counter to the decentralized, autonomous ethos of Yearn. If the management of a mono-team fails, the entire DAO fails with it.
*   **Splinter the DAO completely:** We also considered breaking up the DAO entirely, allowing individual teams or products to spin out as independent entities. This was rejected because it would be massively value-destructive. The Yearn brand carries immense weight, trust, and recognition in the ecosystem, these are assets that have been built over years. Throwing that away would be a disservice to the protocol and all YFI holders.

### 4.2 Out of Scope

- The specific tokenomics of stYFI and revenue distribution mechanics (covered in Part II).
- The allocation of treasury YFI for contributor and team incentives (covered in Part III).

### Background

Yearn's current operational framework is the product of a multi-year evolution aimed at increasing decentralization and contributor autonomy. The foundational shift occurred with the passage of **YIP-61: Governance 2.0**[[1]](#References), which dissolved a centralized operational group in favor of empowering smaller, independent teams (yTeams).

Initially, budget approvals were handled by a dedicated **yBudget** team. Over time, this process evolved further to decentralize decision-making, leading to the current **yBudget II council process**. In this system, all yTeams vote on contributor budget requests (BRs), with revenue-generating teams wielding outsized influence proportional to the revenue they contribute.

This model proved highly effective at instilling fiscal discipline and reducing operational overhead. By giving revenue-generating teams a stronger voice, the DAO successfully aligned its spending with its earnings, leading to significant cost reductions over the past year, essentially cutting the budget in half.

| Metric | yBudget II Epoch 1 (May-Jul 2024) | yBudget II Epoch 5 (May-Jul 2025) | Change |
| :--- | ---: | ---: | ---: |
| **Total Contributor Expenses** | $1,740,000 | $858,000 | **-50.7%** |
| **Average Monthly Expenses** | $580,000 | $286,000 | **-50.7%** |

However, as the DAO has matured, this structure has presented a new set of second-order challenges that now impede our efficiency and focus:

*   **Organizational Misalignment:** The system has seen an increase of non-revenue-earning teams relative to revenue-earning ones. While these teams perform necessary functions, it gives greater influence to initiatives that do not directly impact the bottom line, diluting the focus on profitability.
*   **The Free-Rider & Attribution Problem:** It is difficult to measure and attribute the value created by non-revenue teams. This creates a potential "free-riding" effect by Revenue Teams, where they benefit from the efforts of non-revenue teams, without this being attributed to the right place. This makes it difficult to assess true net profitability of efforts.
*   **Coordination Inefficiency:** The proliferation of many small yTeams, often with overlapping contributors, makes cross-team coordination complex and inefficient. This fragmentation hinders our ability to execute large, cohesive strategic initiatives.

These challenges indicate that while the `yBudget II` process was a successful evolutionary step for instilling fiscal discipline, the next phase of Yearn's growth requires a more streamlined, explicitly revenue-focused operational model. This proposal builds on the successes of the past while directly addressing its emergent limitations.

## Specification
### Overview
This proposal outlines the operational and financial restructuring of the Yearn DAO to focus all efforts on revenue generation and on-chain accountability.

**IMPORTANT NOTE:** This proposal is the first of three interconnected parts of a single initiative designed to overhaul Yearn's operations, tokenomics, and contributor incentives.

- **Part I: Operations & DAO Restructuring (This Proposal)**
- [Part II: stYFI Tokenomics & Migration](https://gov.yearn.fi/t/yip-88-governance-overhaul-styfi/)
- [Part III: Contributor & Team Incentives](https://gov.yearn.fi/t/yip-88-governance-overhaul-incentives/)

All three parts will be discussed in parallel on the forum but will be voted on as a single, all-or-nothing package in one Snapshot vote for **YIP-XX**. If the unified proposal passes, all three parts will be implemented. If it fails, none will be.


### Rationale
TODO: Add Rationale.

### Technical Specification
### 5. Specification (DAO Restructuring)

**This section defines the new operational structure of the DAO, centered on revenue generation and on-chain accountability.**

### 5.1 Revenue Teams & Focus

1.  **Core Principle**: The DAO's primary goal is to generate revenue. All teams must orient their operations around this principle.
2.  **Revenue Teams Defined**: A "Revenue Team" is a team whose core purpose is to generate protocol revenue. This includes teams responsible for vault strategy performance, product development, and product marketing.
3.  **Mandatory Organizational Shift**: All teams must reorganize to align with the Revenue Team model.
4.  **Transition Deadline**: The transition to the new structure must be completed by **October 31, 2025 at 23:59:59 UTC**. Teams that are not revenue-oriented or that fail to align by this deadline will no longer be funded on a recurring basis.
5.  **One-Off Project Funding**: Non-recurring (and potentially non-revenue earning) work may still be funded via a direct BR. Such proposals must be for a specific project with a defined scope and end date, and not for ongoing contributor roles.

### 5.3 DAO Operations (DAO-ops) Team

7.  **Scope Definition**: A single, non-revenue team, DAO-ops, will be maintained with a minimal scope, limited to:
    *   Create and Maintain DAO smart contracts (governance, treasury, rate providers, auctions, YFI tokenomics, etc.).
    *   Build and Maintain DAO governance and reporting infrastructure (budgets, proposals, treasury, voting, etc.).
    *   Performing essential administration directly related to the above tasks, like tweaking parameters, kicking auctions, and optimizing performance of these systems.
8.  **Technical Focus**: The DAO-ops team mandate is strictly technical and administrative. It does not manage community, marketing, social media, or communications, nor does it influence the strategy of revenue-earning teams.
9.  **Budget Approval**: The DAO-ops team must submit a formal Budget Request (BR) for approval following the passage of this YIP to secure funding and commence its work, and will need to continue to submit BRs on an ongoing basis as any other team.

### 5.4 Revenue & Financial Reporting

10. **On-Chain Revenue Splitters**: All team-generated revenue must be sent to designated splitter contracts on Ethereum mainnet. Teams are responsible for bridging funds to Ethereum mainnet in order to send to splitter contracts.
11. **Initial Routing**: Initially, all splitters will be configured to route 100% of incoming revenue to the Yearn Treasury. This will be updated per the routing rules in Part II.
12. **Approved Revenue Tokens**: Revenue must be sent in a format pre-approved by the DAO-ops team (e.g., stablecoins, WETH).
13. **Mandatory On-Chain Reporting**: All budget requests must be justified by on-chain financial reporting that tracks total revenue contributed versus total budget utilized for that team.
14. **On-Chain Budget Requests**: All team budget requests will ultimately be submitted on-chain using a standardized format to be defined by the DAO-ops team.

### 5.5 Budgeting Process & Governance

15. **Proposing New Revenue Teams**: Any group may propose a new revenue-earning team, which must commit to the mandatory on-chain reporting framework.
16. **Budget Request (BR) Cadence**: As already is in place, team BRs will continue to be approved for a maximum duration of **three months**.
17. **Fund Streaming**: Approved budgets will by default be streamed using existing contracts. There will be an option to request up-front payment as part of the BR.
18. **Safeguard Mechanism**: yChad, and subsequently the DAO, will retain the ability to halt fund streams in clear cases of underperformance, malicious activity, or misuse of funds.

#### 5.5.1 Discretionary & Fast-Track Funding
19. **Establishment of a Discretionary Fund**: A dedicated, on-chain fund will be established for urgent, sensitive, or unforeseen expenses that cannot go through the standard public proposal process (e.g., critical security audits, stealth projects).
20. **Initial Funding**: The fund will be initialized with **$250,000** worth of stablecoins from the Treasury.
21. **Management and Delegation**: The fund will be managed by yChad, who has the discretion to delegate its management to another designated multi-sig (or the YBC as described in Part III).
22. **Accountability via Top-Up**: The fund can only be replenished via a formal proposal to the DAO. Such proposals must be accompanied by a report justifying past expenditures and are subject to a DAO vote.

#### 5.5.2 Transition to On-Chain Governance
23. **Interim Budget Governance**: Following the transition deadline, budget approvals for the new revenue teams, the DAO-ops team, and any other proposal will continue to be decided by the existing yBudget II council process.

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## References
1. https://gov.yearn.fi/t/yip-61-governance-2-0/10724
2. https://docs.yearn.fi/ydao/ybudget/ybudget-ii
3. https://gov.yearn.fi/t/yip-64-vesting-yearn-core-contributors/11269
4. https://gov.yearn.fi/t/yip-57-incentivize-yearn-developers/10070
5. https://gov.yearn.fi/t/yip-74-yfi-wintermute-loan-crv-plans/13581
6. https://gov.yearn.fi/t/yip-81-ops-accelerator/14280

## References (Additional)
- https://gov.yearn.fi/t/yip-88-governance-overhaul-styfi/14552
- https://gov.yearn.fi/t/yip-88-governance-overhaul-incentives/14551

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
