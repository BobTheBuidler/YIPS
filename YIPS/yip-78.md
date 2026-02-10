---
yip: 78
title: Partial Compensation Sonne Hack Victims
author: Yearninger
discussions-to: https://gov.yearn.fi/t/yip-78-partial-compensation-sonne-hack-victims/14103
status: Rejected
created: 2024-07-25
---

## Simple Summary
Provide partial compensation for yvUSDT and yvDAI vault users impacted by the Sonne Finance exploit using YFI distributed with a 6-month vesting schedule.

## Abstract
This proposal covers 80% of the remaining losses from the Sonne Finance exploit affecting yvUSDT and yvDAI on Optimism. It requests approximately 58.86 YFI (about $297,439.67 at the referenced date) to compensate depositors, with recipients accepting a 10% loss and assigning future recoveries to the DAO.

## Motivation
Compensating affected users maintains trust in Yearn's stablecoin vaults and acknowledges risk management shortcomings that contributed to the loss exposure.

## Specification
### Overview
- Compensate 80% of remaining losses.
- Pay in YFI with linear vesting over 6 months.
- Users assign all future Sonne recoveries to the DAO.

### Rationale
- Demonstrate depositor protection without fully socializing losses.
- Align recipients with Yearn by paying in YFI with vesting.

### Technical Specification
1) Loss accounting
- yvUSDT net loss: 185,291.61 USDT.
- yvDAI net loss: 145,196.92 DAI.
- Total net loss: 330,488.53.

2) Compensation terms
- Users absorb 10% loss (33,048.85).
- Yearn compensation: 297,439.67 (approx. 58.86 YFI as of Aug 15, 2024).
- Vesting: 1/6 released monthly over 6 months (~9.8 YFI/month).

3) Distribution mechanics
- Depositor snapshot and merkle proof derived from the provided list.
- Vesting distributor contract based on the referenced merkle distributor with vesting.

### Test Cases
Not applicable.

### Configurable Values
- YFI price used for USD conversion.
- Vesting schedule parameters.

## References
- https://gov.yearn.fi/t/yip-78-partial-compensation-sonne-hack-victims/14103
- https://gist.github.com/anyOldDev/b410c4ae27a4e1c3f3de37245205f62f
- https://github.com/pandadefi/merkle-distributor-with-vesting/blob/master/contracts/MerkleDistributor.sol
