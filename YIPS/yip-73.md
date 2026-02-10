---
yip: 73
title: Activate veYFI rewards with oYFI Gauges
author: The members of the "veYFI Secret Admirers" working group
discussions-to: https://gov.yearn.fi/t/yip-73-activate-veyfi-rewards-with-oyfi-gauges/13414
status: Approved
created: 2023-06-27
---

## Simple Summary
Activate veYFI rewards by introducing oYFI and the gauge/epoch system described in YIP-65 so vault users and governors receive tokenomics rewards.

## Abstract
This proposal introduces the oYFI reward token, defines veYFI reward epochs and gauge voting, and activates the veYFI rewards program specified in YIP-65. Rewards are emitted as oYFI, distributed to gauges, and governed by veYFI voting with defined emission and boost mechanics.

## Motivation
Yearn already implemented veYFI governance (YIP-65). This proposal continues that roadmap by rewarding active governors and vault users, strengthening long-term alignment without minting new YFI.

## Specification
### Overview
- Introduce oYFI as the reward token.
- Run emissions in fixed epochs with veYFI voting on gauge allocation.
- Use boost mechanics so vault depositors who also govern receive higher rewards.

### Rationale
- Rewards should go to active protocol users and governors, not passive holders.
- Emissions should adapt to governance participation and lock rates.
- Boost penalties discourage large depositors who do not participate in governance.

### Technical Specification
1) oYFI token
- oYFI is an ERC-20 token redeemable for YFI in exchange for ETH.
- oYFI supply must not exceed the redeemable YFI available to the program.
- Redemption applies a discount to the spot YFI/ETH price using the formula:
  - discount = c/(1 + a * e^k(s*x - 1))
  - c = 1, a = 9.9999, k = 4.6969, s = configurable scaling factor, x = veYFI_supply / YFI_supply
- ETH received from redemption is routed to automated YFI buybacks.

2) Epochs
- veYFI epochs are 14 days and start Thursday 00:00:00 UTC.
- Epochs are synced with Curve veCRV and yETH epochs.

3) Emissions
- Rewards are paid in oYFI.
- oYFI emission per year is approximated by:
  - oYFI_emitted = c * sqrt(veYFI_supply)
  - c is a configurable scaling factor.

4) Gauges
- Gauges are ERC-4626 vaults that accept Yearn vault tokens.
- Users earn oYFI based on boost (1x to 10x).
- Rewards forfeited by users below max boost are allocated to veYFI lockers.
- Boost weighting is computed as:
  - weight = min(balance, 9/10 * total * veYFI_balance/veYFI_total + balance/10)

5) Voting
- Voting occurs in the second half of each epoch with linear weight decay in the final 24 hours.
- 10% of emissions are reserved (5% YFI/ETH liquidity, 5% oYFI/ETH liquidity); the other 90% is allocated by veYFI votes.
- Blank votes remove rewards from the current epoch and either burn them or carry to the next epoch (configurable split).
- Governance proposals require >= 50% majority and a configurable quorum; any address with 1 veYFI or more may submit.

### Test Cases
Not applicable; this proposal defines protocol mechanics and relies on audited implementations.

### Configurable Values
- oYFI discount scaling factor (s).
- Emission scaling factor (c).
- Blank vote burn vs carry percentage.
- Governance quorum.

## References
- https://gov.yearn.finance/t/yip-65-evolving-yfi-tokenomics/11994
- https://gov.yearn.finance/t/yip-56-buyback-and-build/8929
- https://github.com/yearn/veYFI
- https://chainsecurity.com
