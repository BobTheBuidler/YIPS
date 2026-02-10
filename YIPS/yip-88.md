---
yip: 88
title: Governance Overhaul: DAO Restructuring, stYFI, and Incentives
author: 0xPickles and the governance team contributors
discussions-to: https://gov.yearn.fi/t/yip-xx-governance-overhaul-dao-restructuring/14553
status: Proposed
created: 2025-09-28
---

## Simple Summary
Adopt a three-part governance overhaul: restructure the DAO around revenue teams, replace veYFI with stYFI and a 90/10 revenue split, and deploy treasury YFI for contributor incentives.

## Abstract
This proposal combines three coordinated changes: (1) reorganize Yearn teams around revenue accountability and on-chain reporting, (2) introduce stYFI as the liquid governance token with revenue sharing and a veYFI migration plan, and (3) allocate roughly 1,930 YFI for contributor vests, performance bonuses, and a long-term builder collective.

## Motivation
The DAO needs tighter alignment between revenue, governance, and incentives. veYFI participation is low and technically risky, and contributors need clear long-term incentives tied to protocol success. This proposal creates a simpler governance token, a revenue-focused org model, and a transparent incentive framework.

## Specification
### Overview
- Part I: DAO restructuring and on-chain accountability for revenue teams.
- Part II: stYFI tokenomics, revenue sharing, and veYFI migration.
- Part III: contributor incentives funded by existing treasury YFI.

### Rationale
- Revenue-focused teams improve accountability and budgeting.
- stYFI reduces complexity and improves governance participation.
- Incentive programs retain talent and tie rewards to profitability.

### Technical Specification
1) DAO restructuring (Part I)
- Transition deadline: October 31, 2025 23:59:59 UTC; non-revenue teams lose recurring funding after that date.
- DAO-ops team scope: governance/treasury contracts and reporting infrastructure only.
- All team revenue routed to on-chain splitters; initial routing 100% to treasury.
- Budget requests (BRs) remain at max 3-month cadence; future on-chain governance to replace yBudget II.
- Discretionary fund: $250,000 stablecoins managed by yChad (or delegate); refill only via DAO vote.

2) stYFI tokenomics and migration (Part II)
- Stake YFI 1:1 to receive stYFI.
- Unstaking requires a 14-day cooldown; cooldown resets if restarted.
- Governance epochs cannot be shorter than 14 days; stYFI is sole governance token.
- Revenue split: default 90% to stYFI stakers, 10% to treasury (configurable).
- Rewards paid in a single Yearn vault token selected by DAO-ops.
- Voting APR boost allowed, but non-voters may not be reduced by more than 60%.
- veYFI snapshot block: 23460759. veYFI holders must opt in to migrate.
- Migrating veYFI holders receive a decaying reward multiplier (up to 2x for 4-year locks).
- Redemption facility for liquid locker tokens funded by the incentive pool.

3) Contributor incentives (Part III)
- Total incentive pool: ~1,930 YFI (~1,700 YFI from YIP-57 + ~230 YFI veYFI remainder).
- Core contributor vests: up to 1,111 YFI, 3-year linear vesting, 6-month cliff, clawback by yChad.
- Performance bonuses: quarterly YFI based on net profit; bonus cap 50% of net profit.
- Bonus split default: 67% to team, 33% to Yearn Builder's Collective (YBC).
- YBC: long-term stYFI pool for whitelisted contributors; initial seed up to 200 stYFI.
- Contributor delegation vault (new yvYFI) stakes to stYFI and votes for depositors.

### Test Cases
Not applicable.

### Configurable Values
- Treasury/stYFI revenue split.
- Governance epoch length (>= 14 days).
- Voting yield-boost mechanics and caps.
- Performance bonus split and growth-rate cap.

## References
- https://gov.yearn.fi/t/yip-xx-governance-overhaul-dao-restructuring/14553
- https://gov.yearn.fi/t/yip-88-governance-overhaul-styfi/14552
- https://gov.yearn.fi/t/yip-88-governance-overhaul-incentives/14551
