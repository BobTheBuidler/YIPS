---
yip: 74
title: YFI Wintermute Loan & CRV Plans
author: Callen Wintermute (@Callen_Wintermute)
discussions-to: https://gov.yearn.fi/t/yip-74-yfi-wintermute-loan-crv-plans/13581
status: Voting
created: 2023-08-13
---

## Simple Summary
Approve a 12-month, 350 YFI loan to Wintermute with CRV collateral deployed into the yCRV-CRV pool and additional multisig safeguards.

## Abstract
This proposal requests a 12-month YFI loan to Wintermute at 0.10% interest and outlines Wintermute's plan to deploy up to 3M CRV into yCRV liquidity on Yearn/Curve. The updated terms add collateral custody in a shared multisig, a 12-month staking commitment, and a 6-month early return option.

## Motivation
The proposal aims to improve yCRV liquidity and peg stability while enabling Wintermute to continue market-making operations without selling borrowed YFI. It also adds collateral and governance safeguards in response to community concerns.

## Specification
### Overview
- Loan 350 YFI to Wintermute for 12 months at 0.10% interest.
- Deploy up to 3M CRV into yCRV and the yCRV-CRV pool.
- Hold CRV collateral in a shared multisig with Yearn signers.

### Rationale
- Improve yCRV liquidity and rebalance the yCRV/CRV pool.
- Maintain YFI exposure without market selling.
- Add collateral controls to address risk concerns.

### Technical Specification
1) Loan terms
- Amount: 350 YFI.
- Term: 12 months.
- Interest: 0.10%, paid in kind at term end.
- Use: delta-neutral trading only (no farming/lending/voting).

2) CRV deployment
- Use up to 3M CRV to buy yCRV and deploy to the yCRV-CRV pool.
- Stake at least 6 months; updated proposal extends staking to 12 months.
- Optionality to swap lp-yCRV to vl-yCRV.

3) Collateral custody and approvals
- CRV/yCRV (or related variants) held in a 3/4 or 4/6 multisig with Wintermute and Yearn signers.
- No transaction may execute without at least one Yearn signer.
- Yearn signers agree to approve actions within the Yearn + CRV ecosystem.
- After 6 months, Wintermute may return YFI early and receive collateral back.

4) Implementation
- Transfer 350 YFI to Wintermute: 0xDBF5E9c5206d0dB70a90108bf936DA60221dC080.

### Test Cases
Not applicable.

### Configurable Values
- Loan duration and interest rate.
- CRV amount and staking duration.
- Multisig threshold.

## References
- https://gov.yearn.fi/t/yip-74-yfi-wintermute-loan-crv-plans/13581
