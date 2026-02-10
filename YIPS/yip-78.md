---
yip: 78
title: Partial Compensation Sonne Hack Victims
author: anyOldDev (@anyOldDev)
discussions-to: https://gov.yearn.fi/t/yip-78-partial-compensation-sonne-hack-victims/14103
status: Rejected
created: 2024-08-16
---

## Simple Summary
This proposal asks Yearn to partially compensate users of the yvUSDT and yvDAI vaults impacted by the Sonne Finance exploit, via a vested YFI distribution.

## Abstract
This proposal asks Yearn to partially compensate users of the yvUSDT and yvDAI vaults impacted by the Sonne Finance exploit, via a vested YFI distribution.

## Motivation
The Sonne Finance exploit resulted in losses to Yearn’s yvUSDT and yvDAI vault users. This proposal seeks partial compensation while keeping the treasury impact bounded and aligning recipients with Yearn via vested YFI.

## Specification
### Overview
# [Proposal]: Partial Compensation for yvUSDT and yvDAI Vault Users Affected by Sonne Finance Exploit

### Rationale
The rationale is to provide partial restitution for affected vault users while limiting the treasury burden and using vested YFI to align recipients with the protocol’s long‑term health.

### Technical Specification
We propose the following compensation structure:

  1. Total remaining loss: $330.488,53
  2. Affected users to bear 10% of the loss: $33,048.85
  3. Requested compensation from Yearn: $297.439,67 (in YFI equivalent, which represents as of August, 15 2024, a total of 58.86 YFI) 
  4. Users will assign all future recoveries provided by Sonne Finance to the Yearn DAO. 
  5. Users receive compensation in the form of YFI tokens. Despite Users having originally invested in stablecoin vaults Users are willing to align themselves with Yearn and agree to the YFI compensation being subject to a vesting schedule. 
  6. The vesting schedule releases lineary one-sixth (1/6) of the total tokens each month over a period of 6 months. One-sixth of 58.86 YFI amounts to approximately 9.8 YFI potentially sold by users per month, which should have no impact on the YFI price as several thousand YFI are traded on various exchanges daily

Users are then fully aligned with the objective of Yearn. 

Yearn's Financial Position: 
As of August 16, Yearn's financial position is as follows:
  
Total liquid assets: $32.7M 

The proposed compensation of $297.439,67 represents approximately 0.9% of Yearn's total liquid assets as of August 16, 2024, a manageable amount that won't jeopardize Yearn's financial stability. 

[Note: Following Yearn's recovery efforts and yvOP compensation, affected WETH and USDC vaults suffered total losses of 1% or less. Hence, they are excluded from this proposal, since the losses lie underneath the accepted loss of 10%.]

Process of executing the proposal if voted "yes":

A. full list of depositors -> [https://gist.github.com/anyOldDev/b410c4ae27a4e1c3f3de37245205f62f](https://gist.github.com/anyOldDev/b410c4ae27a4e1c3f3de37245205f62f)
It's a balance snapshot of the vault and the rewards contract combined done using the graph.
B. smart contracts -> [https://github.com/pandadefi/merkle-distributor-with-vesting/blob/master/contracts/MerkleDistributor.sol](https://github.com/pandadefi/merkle-distributor-with-vesting/blob/master/contracts/MerkleDistributor.sol)
The contract is a merkle-distributor forked from uniswap wich has been modiifed to create a vesting contract using llamapay contracts.
C. merkle proof -> Yearn will have to create based on the price of YFI and the  full list of depositors as disclosed in the link above.
D. Yearn (or alternatively the Team behind the proposal) will have to convert the USD amount to YFI amount, generate the merkle proof based on the information provided in the shared links and deploy the contract
E. The team behind the proposal will help if necessary to create the merkle proof once the YFI price for compensation has been decided.

### Test Cases
Not applicable.

### Configurable Values
- Total remaining loss: $330,488.53.
- User loss share: 10% ($33,048.85).
- Requested compensation: $297,439.67 (in YFI, ~58.86 YFI at the referenced price).
- Vesting schedule: 6 months, releasing 1/6 per month.
- Compensation token: YFI (vested).

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
