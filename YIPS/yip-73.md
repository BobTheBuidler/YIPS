---
yip: 73
title: Activate veYFI rewards with oYFI Gauges
author: The members of the "veYFI Secret Admirers" working group
discussions-to: https://gov.yearn.fi/t/yip-73-activate-veyfi-rewards-with-oyfi-gauges/13414
status: Approved
created: 2023-06-27
---

## Simple Summary
Introduce the oYFI token for use in the veYFI gauges  outlined in YIP-65, define processes, deployment, and the transition towards full immutability.

## Abstract
**If approved**, this proposal will:
* Introduce the oYFI token.
* Assign oYFI as the reward token for vault gauges.
* Establish the emission of oYFI rewards based on the veYFI lock rate.
* Detail the launch specifications for veYFI rewards.
* Define veYFI epochs and voting.
* Set up guidelines for the eventual transition to full immutability.

## Motivation
This proposal continues Yearn's implementation of YIP-65. Previously, the protocol was upgraded to enable YFI holders to vote-escrow their YFI and thus autonomously receive YFI rewards for committing to help govern the protocol (constantly increasing active governors’ relative share of governance power and kickstarting a decentralized governance flywheel).

With this YIP, YIP-65 continues by boosting the governance rewards of veYFI holders (governors) who also happen to be Vault depositors—this ensures that the most committed Yearn community members increase their governance power at an even faster rate, deepening the governance flywheel and helping maximize the protocol’s autonomy.

Approving this proposal won’t make you richer, but it will ensure that those most committed to governing and using the system will steadily increase their governance power, keeping Yearn on track to be a fully self-governing protocol.

### Epochs

Just like Curve Finance's seminal veCRV design, veYFI uses epochs to redirect rewards frequently as determined by veYFI voters. This responsiveness allows the model to adapt to changing needs.

### veYFI Rewards Emission

The emission of bought back YFI is inspired by the Ethereum staking emission model.[[7]](#References) Instead of validators, the driving variable is the amount and duration of YFI locked in veYFI.

The rationale is to act as a dampening function on both extremes of the spectrum; as more YFI is locked, the rewards per veYFI can decrease. Similarly if less YFI is locked, the rewards per veYFI increase.

As there is no minting of new tokens, the emission model is conservative to ensure rewards last longer.

Through blank voting, veYFI holders have the power to postpone emission slated for an epoch into the future, in order to further conserve emission and extend the runway of the tokenomics program.

### veYFI Gauges and Boost Penalties

The rewards we emit are to gauges where yearn vault tokens are staked, ensuring that only genuine users of yearn protocols receive rewards. 

However, we do want to discourage large depositors from monopolizing rewards unless they are actively involved in yearn governance.

This is achieved through a modified form of boost, pioneered by Curve Finance and Michael Egorov, where gauge depositors must hold veYFI in proportion to their share of deposits in a gauge to maximize their rewards. The difference is paid as penalties to veYFI holders.

### oYFI

To avoid rewarding predatory users who farm tokens only to sell them off, we propose oYFI, partially inspired by a design proposed by Andre Cronje for the K3PR protocol.[[8]](#References)

oYFI allows its holder to obtain bought back YFI at a discount from the current spot market price, with the discount rate varying based on the proportion of veYFI locked.

As more veYFI is locked, the discount decreases. When veYFI decreases, discount increases to attract more locking.

The proceeds are then routed towards more YFI buybacks, improving the sustainability and longevity of the program.

### Considerations

Refer to YIP-65 for additional related considerations.

#### Future Possibilities

* Tokenomics program could be utilized as a "liquidity for hire" model where protocols remunerate yearn users to channel liquidity into their pools.
* Introduction of incentive programs to drive specific results or emission votes.
* Usage of epochs and voting process for passing YIPs and governance proposals that aren't related to tokenomics.
* Expansion of veYFI's "useful work", perhaps acting as emergency protocol backstops, parameter tuning, and operational management of vaults.
* Adding more pathways for emissions and penalties to stimulate the effective governance of the yearn protocol suite.
* Further enhancing the "skin in the game" for YFI token holders to ensure their actions and decisions deeply impact the performance of the yearn protocol suite.

#### Risks

* A potential flaw in the tokenomics model design or implementation could lead to unexpected reward behavior or loss of funds.
* The introduction of low-quality veYFI gauges may result in rewards being redirected there, leading to less benefit to the yearn protocol.
* The tokenomics model may not attract enough Total Value Locked (TVL) to sustain future rewards with buybacks and may need to be reassessed at some point.
* Changes to rewards and emission parameters made by veYFI voters could result in suboptimal behavior and performance.

#### Alternatives Considered

* Rewarding unlocked YFI: This was avoided to mitigate the risk of disbursing YFI to users who are not interested in holding the token for governance purposes. 
* Directing rewards to veYFI lockers directly: This was avoided to ensure that rewards flow to active rather than passive protocol participants, i.e., users of yearn vaults.
* Restricting third-party protocols from building on top of the tokenomics program: This was avoided in favor of creating a contract-friendly, permissionless block for others to build upon. We explicitly welcome additional third parties to build on top of the yearn suite of protocols.

### Background

### YFI Buybacks

The total supply of YFI tokens is 36,666, which has been completely distributed. Following the adoption of YIP-56[[1]](#References), YFI tokens are bought back from the open market using earnings from yearn vaults. This process is automated, and as of this writing, about $23.7 million USD equivalent has been used to purchase 1,311 YFI, averaging a price of $18,100 per token.[[2]](#References)

### Tokenomics post YIP-65

YIP-65[[3]](#References) outlined a roadmap for the future of YFI tokenomics. Following this, veYFI was introduced[[4]](#References), enabling YFI tokens to be "vote escrowed" for up to four years. This token, veYFI, controls yearn governance. This proposal aims to activate section 2.3 of the YIP-65 spec, "Vault gauges + Voting", using oYFI as a new type of reward token.

### Summary of the veYFI Tokenomics Program

Users can lock YFI as veYFI for up to four years to control yearn's governance proportionally to the duration-weighted amount of their lock. They can exit this lock early, paying a penalty of up to 75% of their locked YFI, which is proportionally allocated to remaining veYFI lockers.

Tokenomics rewards are in the form of oYFI, a token that allows its holder to buy back YFI at a discount. The discount rate depends on the amount of veYFI currently locked in the protocol. Rewards are distributed over epochs, with the total rewards per epoch also determined by the amount of veYFI locked in the protocol.

In every epoch, veYFI voters allocate the distribution for the next epoch to oYFI gauges. Each gauge receives an amount of oYFI according to the votes received in the previous epoch. Yearn vault depositors stake their vault tokens into oYFI gauges to earn oYFI. The earned oYFI amount is determined by the user's "boost", their share of gauge TVL in relation to their share of veYFI. Users with boosts that is below the max forfeit some of their oYFI rewards to veYFI lockers.

In summary, gauge depositors earn oYFI according to their boost. veYFI holders earn YFI from users who exit their locks early, and oYFI from gauge depositors who do not hold max boost.

### Implementation

A working implementation is available in the yearn/veYFI repository[[5]](#References) and has been audited by ChainSecurity.[[6]](#References) Post-audit, a configurable scaling factor `s` has been added to oYFI, and `x` has been adjusted to avoid short duration locks biasing the formula.

### Out of Scope

* This proposal **does not** involve minting new YFI tokens; rewards in this system consist solely of tokens purchased from the open market.
* This proposal **does not** attempt to promote YFI as an attractive investment; its purpose is to redistribute governance power to the most active community members and protocol users.
* This proposal **does not** aim to increase yearn treasury holdings; instead, it ensures bought back YFI is redistributed back to protocol users and YFI token holders.

## Specification
### Overview
Introduce the oYFI token for use in the veYFI gauges  outlined in YIP-65, define processes, deployment, and the transition towards full immutability.

### Rationale
TODO: Add Rationale.

### Technical Specification
**Note:** The spec outlines the desirable end state. Some compromises may need to be made during the rollout before the final state is reached. Refer to Section 8 below.

### 0. Definitions

* YFI: Unlocked YFI token
* veYFI: YFI token locked for a duration of up to 4 years (208 weeks), where `veYFI = YFI * lock_duration_as_share_of_max`. For example, 100 YFI locked for 1 week equals 100 x (1/208) ~= 0.48 veYFI. This operates as per the contract deployed[[9]](#References) with the passing of the proposal to activate veYFI.[[4]](#References)

### 1. oYFI

1. Is a token that implements the ERC-20 standard.
2. Gives its bearer the right to redeem an equivalent of YFI, in exchange for ETH.
3. oYFI is burned upon redemption.
4. The circulating supply of oYFI must not exceed the amount of YFI that is available to be redeemed as part of the tokenomics program.
5. The amount of ETH required for redemption is at a discount of the current spot price of YFI/ETH.
6. Discount calculation is an approximation of the following formula:
    ```
    discount = c/(1 + a * e^k(s*x − 1)), where
    c = 1
    a = 9.9999
    k = 4.6969
    s = configurable scaling factor
    x = veYFI_supply / YFI_supply
    ```
7. ETH received from oYFI redemption is redirected to automated YFI buybacks that are handled by an immutable smart contract, like the one already in production for DAI.[[2]](#References)

### 2. Epochs

1. veYFI epochs last for 14 days, commencing on Thursdays 00:00:00 UTC.
2. Epochs are synced to coincide with Curve's veCRV epochs and yETH's epochs.

### 3. Emission

1. Rewards are paid as oYFI.
2. These rewards are distributed to Gauges (see below) at the beginning of each epoch.
3. The annual rewards emission is calculated as an approximation of the following formula:
    ```
    oYFI_emitted = c * sqrt(veYFI_supply), where
    c = configurable scaling factor
    ```

### 4. Gauges

1. A gauge is an ERC20 token and vault that implements the EIP4626 standard.
2. Users deposit yearn vault tokens to earn oYFI rewards according to their boost.
3. Boost ranges from 1-10x and determines a user's share of rewards. Positions with less than a 10x max boost forfeit a share of their oYFI rewards. At best, a user with a 10x boost earns 100% of their rewards; at worst, a user with a 1x boost forfeits 90% of rewards.
4. Forfeited oYFI are proportionally allocated to veYFI lockers as additional rewards.
5. The earning weight (`current_boost/max_boost`) is calculated in the same way as in Curve[[10]](#References), when accounted for a 10x max boost instead of Curve's 2.5x:
    ```
    weight = min(Gauge.balanceOf(user), 9/10 * Gauge.totalSupply * veYFI.balanceOf(user)/veYFI.totalSupply + Gauge.balanceOf(user)/10)
    ```

### 5. Voting

1. veYFI holders vote on gauge emission and governance proposals.
2. Voting takes place in the second half of the epoch.
3. To discourage last-minute voting, there is a linear decay of voting weight in the final 24 hours of the epoch, reaching 0% voting weight at the last block of the epoch.

#### 5.4 Gauge emission votes

1. Gauge emission votes set the distribution of oYFI allocated in an epoch, determining which specific gauge should receive what portion of oYFI emissions.
2. 10% of an epoch's total emission is allocated to specific gauges: 
* 5% of total to encourage YFI/ETH liquidity
* 5% of total to encourage oYFI/ETH liquidity
3. veYFI holders vote on the remainder 90% allocation.
4. Voters can cast "blank" votes, which leads to this proportion of oYFI rewards being taken out of the epoch's emission allocation.
5. The blank vote oYFI can be burned, thereby extending the runway of the tokenomics program, or moved to the immediately next epoch's emission allocation, thereby increasing rewards in the next epoch.
6. The amount of oYFI burned vs moved is configurable by a parameter.
7. Voters can cast many votes per epoch, but any gauge can only be voted on once in a single epoch.
8. Votes reset at the start of a new epoch; there is no carry-over of votes between epochs.

#### 5.5 Governance proposals

1. Governance proposals include, but are not limited to:
 * Adding new gauges
 * Removing existing gauges
 * Changing parameters
2. Proposals can be submitted in the first half of the epoch.
3. Proposal submission occurs in a dedicated Yearn governance forum section.
4. Any address holding 1 veYFI or more is able to submit a governance proposal.
5. Governance proposals pass by simple majority (>50% of the veYFI vote).
6. There is a configurable quorum parameter, a minimum amount of veYFI that needs to vote in favor for a governance proposal to pass, regardless of the number of votes in support.

### Figure 1. Epoch Timeline Illustration
```
|------week-1------|-----week-2-----|------week-3------|-----week-4------|...
| epoch n                           | epoch n+1...
| proposals n+1    | vote n+1       | proposals n+2    | vote n+2...
                                  x vote power decay
                                    x distribute n+1 rewards to gauges
```

### 6. Configurable parameters

These are the parameters that veYFI holders can adjust via governance proposals.

| Parameter | Description | Configurable Range | Default |
|---|---|---|---|
| Quorum | The minimum amount of veYFI needed to approve a governance proposal | 0-10_000 veYFI | 10 veYFI |
| Blank Vote Burn | The percentage of oYFI from blank gauge emission votes that are burned instead of moving to the next epoch | 0%-100% (100% means all oYFI is burned; 0% means all oYFI transfers to the next epoch) | 50% |
| `s` | Scaling factor for oYFI discount | 1.00 - 12.00<sup>❉</sup> | 10.00 |
| `c` | Scaling factor for oYFI emission | 4 - 64<sup>❉</sup> | 12 |
| YFI Gauge | The gauge that gets at least 5% emission for YFI liquidity | `address` | YFI/ETH Curve LP yVault |
| oYFI Gauge | The gauge that gets at least 5% emission for oYFI liquidity | `address` | oYFI/ETH Curve LP yVault |

<sup>❉</sup> _Change is applied with linear scaling over the course of an epoch to prevent front-running._

### 7. Launch Steps

If this YIP is approved, the following steps will be taken to launch the programme:

1. **Epoch 1 voting snapshot announcement:** One week in advance, a timestamp for the first Epoch's vote is announced. This allows users to lock YFI into veYFI to participate.
2. **Deploy oYFI.**
3. **Seed oYFI/ETH:** Determine the value of oYFI (its YFI discount) based on the snapshot veYFI balance for Epoch 1. Mint $5k worth of oYFI and seed it with an equivalent amount of ETH in a Curve v2 pool. 
4. **Deploy initial gauges:** Launch the initial gauges (see below) as they become available.
5. **Start epoch 1:** Seed gauges with oYFI and prepare for epoch 2 voting.
6. **Apply for oYFI/ETH CRV gauge on Curve.** Attach strategy to oYFI/ETH Curve LP yVault if approved.

#### 7.7 Initial Gauges

1. Gauges for the following tokens are pre-approved for deployment with this YIP:
   * **YFI/ETH Curve LP yVault**
   * **oYFI/ETH Curve LP yVault**
   * **yCRV/CRV Curve LP yVault** (also known as "lp-yCRV")
   * **yBAL/BAL Balancer LP yVault** (also known as "lp-yBAL")
   * **yETH/ETH Curve LP yVault**. This gauge will be deployed once yETH has launched.
2. With the deployment of yearn v3 vaults expected soon[[11]](#References), additional higher-margin and/or strategic veYFI gauges can be considered and green-lit for deployment with the passing of veYFI Governance Proposals.

#### 7.8 Parameters & Fine-Tuning

1. The system launches with the default parameters above.
2. During the first **6 epochs**, yChad can adjust the system, bypassing governance proposals for parameter changes, and circumventing gradual scaling of parameter changes.
3. To bootstrap the oYFI discount curve, `s` starts at a steep `s=10`, with the explicit objective to decrease to `s=2` as the veYFI supply increases following the successful roll out of the programme.

### 8. Towards a Fully Immutable System

1. Initial voting takes place via Snapshot, with yChad implementing changes according to the passed proposals and gauge emission allocations. Some features, like voting decay before epoch expiry, may not be initially implemented. 
2. Initial emission is manual, with oYFI being minted and distributed to gauges.
3. From the start, ETH from oYFI redemption is automatically used for YFI buybacks.
4. The YIP instructs Yearn contributors to make the system fully immutable **before the end of the first 12 epochs**. This involves:
   * Automating and making oYFI minting immutable as per the emission curve
   * Ensuring oYFI supply is handled on-chain so it cannot be unbacked
   * Automating on-chain gauge weight voting and gauge allocation
   * Automating on-chain voting for governance proposal and parameter changes
   * Minimizing yChad's involvement or dependencies wherever possible.
5. Significant changes to the programme before it is made immutable require approval through a new YIP.

### 9. Incentives

1. This YIP doesn't cover incentives for veYFI voting, but such voting is strongly encouraged.
2. If this YIP is approved, Yearn contributors are instructed to consider launching incentive programs for veYFI voting, either on-chain or off-chain. This could be for weight allocations, parameter changes, or general governance proposals. New YIPs are not required to launch such programs.
3. Incentives should be posted during proposal submission periods, not voting periods.

### 10. Use at Own Risk

Participation in the veYFI tokenomics program and Yearn governance is optional and not required to use or interact with the Yearn suite of protocols. Holding YFI or locking veYFI offers no financial gain—it's a governance power redistribution program. Yearn contributors are not responsible for any loss from its use. No guarantees or assurances are provided, and if catastrophic events or security incidents occur, veYFI voters may determine the course of action.

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## References
1. http://gov.yearn.fi/t/yip-56-buyback-and-build/8929
2. https://buyback.yearn.finance/
3. http://gov.yearn.fi/t/yip-65-evolving-yfi-tokenomics/
4. http://gov.yearn.fi/t/proposal-activate-veyfi/
5. https://github.com/yearn/veYFI
6. https://chainsecurity.com/wp-content/uploads/2023/03/Yearn-Smart-Contract-Audit-oYfi-ChainSecurity.pdf
7. https://eth2book.info/capella/part2/incentives/issuance/#overall-issuance
8. https://andrecronje.medium.com/keep3r-redeemable-kp3r-rkp3r-c200fb8740ef
9. https://etherscan.io/address/0x0bc529c00c6401aef6d220be8c6ea1667f6ad93e#code
10. https://resources.curve.fi/reward-gauges/boosting-your-crv-rewards#formula
11. https://github.com/yearn/budget/issues/120

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-74.md@@@
---
yip: 74
title: YFI Wintermute Loan & CRV Plans
author: Callen Wintermute
discussions-to: https://gov.yearn.fi/t/yip-74-yfi-wintermute-loan-crv-plans/13581
status: Proposed
created: 2023-08-13
---

## Simple Summary
Wintermute is excited to put forward this proposal which outlines the motivation, background and terms of a YFI loan to Wintermute Trading and further explains our long-term plans with respect to CRV on Yearn to the Yearn DAO.

## Abstract
Wintermute is excited to put forward this proposal which outlines the motivation, background and terms of a YFI loan to Wintermute Trading and further explains our long-term plans with respect to CRV on Yearn to the Yearn DAO.

Specifically, we are requesting approval of a YFI loan to Wintermute Trading and authorization of a transfer of 350 YFI ($2.18M) from the DAO’s treasury to Wintermute Trading for 12 months at a 0.10% interest rate to be paid in kind at the end of the loan term.

Separately, as part of Wintermute’s continued engagement on Yearn, Wintermute plans to utilise its funds of up to 3M CRV ($1.73M) to buy yCRV and subsequently add and deploy our assets to the yCRV-CRV Curve pool (lp-yCRV V2) on Yearn for a minimum of 6 months.

We believe that this should help rebalance the pool which currently sits at 69%/31% yCRV/CRV, improve the yCRV peg, and increase the pool’s liquidity.

## Motivation
The past 2 weeks have once again tested the resilience of DeFi off the back of a bug in specific versions of Vyper. Subsequently, CRV’s largest source of on-chain liquidity vanished due to the CRV/ETH Curve pool being drained. This once again raised alarm bells for the Aave community as the price of CRV went down and the probability of insolvency inched closer due to Michael’s large CRV position on Aave V2.

With little on-chain liquidity present and multiple loan positions to manage, a series of OTC trades were conducted with various parties across DeFi, including Wintermute Trading. We are now looking to deploy some of the CRV tokens on protocols where CRV is locked perpetually, including Yearn!

We strongly believe in the vision of a truly decentralized world and Yearn has played an extremely positive role in empowering and advancing this vision. Therefore, we’d love to proactively engage with the Yearn community and the DAO by utilising up to 3M ($1.73M) of our CRV to purchase yCRV, and then deploy a mixture of our assets to the yCRV-CRV liquidity pool on Curve which only has [$5.25M](https://curve.fi/#/ethereum/pools/factory-v2-280/deposit) in TVL.

**Wintermute’s Basic Background:**

Wintermute Trading is a leading crypto-native algorithmic trading firm, specializing in creating efficient markets across centralized and decentralized exchanges. Wintermute was founded in July 2017 by three Optiver veterans. Evgeny Gaevoy, founder and CEO, was previously head of ETFs (screen and OTC) at Optiver Europe, one of the largest ETF market-making desks. Since our inception, we have traded over $3T and expanded our presence across 80+ (de)centralized exchanges and various (non)EVM chains, continuously supporting the ecosystem for our partners and their communities.

Alongside our trading arm, Wintermute Ventures and Wintermute Governance support and work with leading crypto projects with the goal of truly adding value, enabling partnerships, and helping shape a positive outcome for the ecosystem. Importantly, we do not target large ownership stakes; decentralized ownership is an important prerequisite to transitioning to a robust future.

## Specification
### Overview
**(21/8/23) Updated Proposal:** 

Hi everyone,

thanks for all the feedback in both the forum and Discord. We’d like to reach a middle ground where both sides are relatively happy but ensure we can keep it as simple as possible.

It’s clear that the largest concern from the community is that the loan has no collateral from our side, which is fair considering the events that have happened over the past year.

So we propose this:

* We retain the same initial plan as before - use up to 3M CRV to buy yCRV, deploy yCRV tokens to the yCRV-CRV pool and stake this on yearn.

* Our CRV (whether that be yCRV, st-yCRV, lp-yCRV, vl-yCRV) will be held in a 3/4 or 4/6 multisig with wintermute folks and core yearn contributors. (No transaction can be made without at least one signature from a yearn member).

* Yearn multisig operators agree to approve anything we do as long as it’s within the Yearn + CRV ecosystem (e.g., swapping to vl-yCRV).

* We will extend our staking duration to 12 months to match the loan duration, however, after 6 months we have the option to return the YFI and receive our collateral back.

This keeps both parties’ commitments rather simple and we provide collateral for our loan.

We also want to reiterate that the loaned YFI will be used solely for our delta-neutral trading, we have no intent to sell it, and it will not be used in the YFI tokenomics ecosystem.

### Rationale
TODO: Add Rationale.

### Technical Specification
**Wintermute’s plans:**

* Borrowed YFI will be used exclusively for trading purposes. No farming, lending, voting, etc.
* Use up to 3M CRV ($1.73M) to buy yCRV (depending on the ratio of yCRV-CRV in the liquidity pool).
* Deploy yCRV tokens to the yCRV-CRV pool which we believe will help rebalance the pool and stake this on Yearn for a minimum of 6 months.

* Has the optionality to swap the lp-yCRV to vl-yCRV for active participation in the Curve Wars.

**Our Ask:**

Wintermute Trading is requesting approval for a 12-month loan of 350 YFI ($2.18M) at a 0.10% interest rate from the DAO’s treasury.

**Loan Repayment:**

Wintermute Trading agrees to return the full 350 YFI loan amount and 0.10% interest paid in kind to the DAO’s treasury at the end of the 12-month period.

#### Implementation

If approved by the Yearn DAO, 350 YFI will be sent from the DAO’s treasury to Wintermute’s address:

* 0xDBF5E9c5206d0dB70a90108bf936DA60221dC080

#### Next Steps

We hope to gauge the community's sentiment on our new proposal by adding a new poll that will run for 2 days. If the poll is relatively positive with the majority of votes being in favour of the new proposal, we will look to formalise this into a YIP and go to a Snapshot Vote.

If the majority of the community is against the proposal as indicated by the poll, unfortunately, we will not move to a Snapshot vote and we thank the community for engaging with us!

# Updated Proposal Poll
* For
* Against

# Old Proposal:

Following community discussion and feedback after 7 days, we will look to initiate a Snapshot Vote with voting options:

1. For - Approve and transfer a loan of 350 YFI to Wintermute Trading.
2. Against - Reject the proposal.

#### Previous Poll

* For
* Against

#### Description

Hi Yearn Community!

Wintermute is excited to put forward this proposal which outlines the motivation, background and terms of a YFI loan to Wintermute Trading and further explains our long-term plans with respect to CRV on Yearn to the Yearn DAO.

Specifically, we are requesting approval of a YFI loan to Wintermute Trading and authorization of a transfer of 350 YFI ($2.18M) from the DAO’s treasury to Wintermute Trading for 12 months at a 0.10% interest rate to be paid in kind at the end of the loan term.

Separately, as part of Wintermute’s continued engagement on Yearn, Wintermute plans to utilise its funds of up to 3M CRV ($1.73M) to buy yCRV and subsequently add and deploy our assets to the yCRV-CRV Curve pool (lp-yCRV V2) on Yearn for a minimum of 6 months.

We believe that this should help rebalance the pool which currently sits at 69%/31% yCRV/CRV, improve the yCRV peg, and increase the pool’s liquidity.

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-75.md@@@
---
yip: 75
title: Launch V3
author: V3 Protocol Team & V3 "Secret Admirers" Group
discussions-to: https://gov.yearn.fi/t/yip-75-launch-v3/13591
status: Proposed
created: 2023-08-15
---

## Simple Summary
Launch the full V3 system - making the latest generation of yield generating vaults and strategies permissionlessly deployable by anyone.

## Abstract
If adopted, this proposal seeks to:

* Ratify the Design Specification of V3 and endorse its deployment.
* Specify parameters and initial configurations.
* Specify the bootstrapping and implementation process.
* Accept Governance roles.

## Motivation
### Background

From the outset, the core goal of V3 development has been to be *a significant upgrade to V2*. The end state of V3 should be a fully decentralized protocol that provides the most secure and trusted infrastructure for on-chain capital allocation.


To achieve this Yearn contributors outlined four key requirements for V3 to fulfill:
* Further decentralization at launch and enable progressive decentralization over time.
* Simplify strategy writing.
* Better than Yearn's V1 single vault/strategy offering.
* Better than Yearn's V2 managed vaults.


#### **Vision**:
Yearn V3 attempts to commoditize what Yearn Vaults V2 does. Management and strategy writing becomes easy for anybody to do. Effectively creating an open marketplace of V3 Vaults and strategies that can be operated by any third party, individual or entity without any involvement from Yearn contributors. Our goal is to provide the base infrastructure that all on chain capital allocators use.

The open design of Yearn V3 creates little reason to launch a full fork. Instead encouraging others to build on top of the Yearn stack. We envision the next generation of yield aggregators will be strategists and vault managers in the Yearn marketplace. Integrating their own tokens and using their marketing, risk management, and developer expertise to attract capital.

The high standards Yearn puts on its own vaults has long been the main growth constraint for the protocol. V3 takes these brakes off. Now anyone both within Yearn and outside can build, deploy and manage their own vaults and strategies with any risk profile they desire. While Yearn contributors may certainly choose to continue running V3 versions of our popular very safe single asset vaults or deploying factory vaults. No gate keeping means V3 allows the flexibility to properly experiment and grow the range of strategies and vaults offered.

Perhaps a protocol with a large idle USDC position in their treasury wants to deploy some of those funds to generate returns. They can manage their own vault picking and choosing which strategies from the marketplace are within their risk profile.

This creates opportunities for new and improved Yearn teams to arise and become even more decentralized. For example a yTeam could become a rating agency where vault managers or strategists pay to be reviewed and get rated. Like a very specialized audit firm.

In V3 strategists can now simply write and deploy strategies fully autonomously and people can start using it immediately. Want it to be included in vault? You can apply for a rating and pitch it to vault managers. 

Different vault managers can have different requirements. Perhaps a Yearn vault will require your strategy to be at or above some specific rating threshold. While a 3rd party vault can have entirely different and unique requirements. Above or below the Yearn standard.

With all this commoditization one might wonder about the impact this will have on Yearn earnings. The unique nature and exclusivity of the V2 design generated significant revenues from vault fees that flowed directly to the Yearn treasury. However, in this commoditized future Yearn can not only generate revenue from vault management but also firmly positions our future to be in market technology capture. 

Why spend the incredible amount of time and money it takes to build, audit and launch your own vault system when you can immediately and cheaply leverage the proven and trusted Yearn stack.

We see this to be a positive shift for the Yearn suite of protocols. We will become more resilient to the swings in the crypto markets, and no longer tied to the success of a few other protocols.  Key teams can transition into independent, peripheral and fully autonomous entities. This evolution opens up possibilities for healthy competition and innovation, leading to a reduction in protocol expenses while cementing its market position no matter what direction the market goes in or which specific applications lead the way.



### Definitions

#### Universal Terms
* Vault - A tokenized representation of a yield bearing position. 
* ERC4626 - A standard for a yield bearing vault.

#### Yearn Terms
* V3 Vault - A yearn-branded ERC4626 "meta vault" that is a debt allocator between multiple different strategies. 
* Strategy - A term that V3 uses to refer to any ERC4626 compliant contract that a V3 Vault balances debt between. A strategy can be another Yearn vault but doesn't need to be. It can be anything that implements the same API as an ERC4626 Vault (e.g. sfrxETH).
* V3 Tokenized Strategy - A technical implementation of a Strategy that is also a stand-alone ERC4626 compliant Vault. These are the yield generators in the V3 ecosystem.

### In Depth

**TLDR**: In V3 both Vaults and Strategies are fully stand alone 4626 compliant vaults. The relationship between a V3 Vault and its strategies is entirely changed and are now fully independent. Meaning not only can a vault deploy capital to many strategies. But now, a strategy can accept capital from many different vaults (as well as non-vault sources, like direct deposits from users).

[Vault Spec](https://github.com/yearn/yearn-vaults-v3/blob/master/TECH_SPEC.md)
[Tokenized Strategy Spec](https://github.com/yearn/tokenized-strategy/blob/master/SPECIFICATION.md)

## Specification
### Overview
**YIP-XX: Launch V3**

### Rationale
TODO: Add Rationale.

### Technical Specification
**1. Relevant Contracts**:

The first release "3.0.0" has been deployed on Ethereum Mainnet, Polygon, Optimism and Avalanche.

Contract Addressses (Constant across all chains):

*Vault BluePrint* (To use EIP-5202) : 0xfC49ca826f8C68c0345410fcA0c7d1e0550d9ee9v

*VaultFactory* : 0xD1736eBbdefae37503F3eD8D718b61a494F24c1D

*TokenizedStrategy* : 0xAE69a93945133c00B9985D9361A1cd882d107622

**2. Configuration**:

2.1 Vault Blueprint:
- n/a

2.2 Vault Factory: 
- MAX_FEE_BPS (constant): 50%
- default protocol fee : 20%
- protocol fee recipient : Chain specific V3/Treasury Splitter Contract.
- governance : yChad or equivalent
- Mainnet will have all V3 vaults that have a V2 equivalent have a custom protocol fee set at 40% of the default fee.

2.3 Tokenized Strategy:
- MIN_FEE (constant): 5%
- MAX_FEE (constant) : 50%

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## References
1. https://github.com/yearn/yearn-vaults-v3
2. https://github.com/yearn/tokenized-strategy
3. https://github.com/yearn/vault-periphery
4. https://github.com/yearn/tokenized-strategy-periphery
5. https://github.com/Schlagonia/Yearn-ERC4626-Router

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-78.md@@@
---
yip: 78
title: Partial Compensation Sonne Hack Victims
author: Yearninger
discussions-to: https://gov.yearn.fi/t/yip-78-partial-compensation-sonne-hack-victims/14103
status: Rejected
created: 2024-07-25
---

## Simple Summary
This proposal aims to provide partial compensation to users of yvUSDT and yvDAI vaults affected by the Sonne Finance exploit. It suggests Yearn cover 80% of the remaining losses, with affected users accepting a 10% write-down. This approach demonstrates Yearn's commitment to users while balancing the interests of YFI holders.

## Abstract
This proposal aims to provide partial compensation to users of yvUSDT and yvDAI vaults affected by the Sonne Finance exploit. It suggests Yearn cover 80% of the remaining losses, with affected users accepting a 10% write-down. This approach demonstrates Yearn's commitment to users while balancing the interests of YFI holders.

## Motivation
This proposal addresses three key issues:

  1. Trust Maintenance: Compensating affected users demonstrates our commitment to depositor safety, crucial for retaining and attracting users.

  2. Long-term Benefits: The goodwill generated will likely outweigh short-term costs, potentially leading to increased deposits and protocol growth.

  3. Acknowledging Risk Management Shortcomings: The incident highlights an overweighted allocation to a protocol where yAudit had identified potential security risks. By approving this proposal, we signal our commitment to improving risk assessment and management practices, thereby better protecting user funds in stablecoin vaults going forward.

### Background

On May 15, 2024, Sonne Finance, where Yearn had allocated significant portions of yvUSDT and yvDAI vault assets, was exploited for $20 million [1]. This occurred despite a prior audit by Yearn-assigned auditors [2]. The exploit targeted a vulnerability in a new governance timelock introduced by Sonne Finance. 

On May 24, 2024, an increased rate of OP rewards was announced by a Yearn contributor [3]. For 4 weeks, these rewards were paid out and mitigated some of the occurred losses. The remaining losses are as follows:

Affected vaults and losses:

1. yvUSDT Vault (Optimism) [4]:
   - Total Gross Loss: 356,996.37 USDT [6]
   - Compensation in OP already received: $171,704.76 (76,195.19 yvOP which is 78,404 OP at a TWAP price during the rewards period of $2.19)
   - Net Loss: 185,291.61 USDT

2. yvDAI Vault (Optimism) [5]:
   - Total Gross Loss: 294,283.36 DAI [6]
   - Compensation in OP already received: $149,086.44 (66,157.90 yvOP which is 68,076 OP at a TWAP price during the rewards period of $2.19)
   - Net Loss: 145,196.92 DAI

Total Net Loss of vaults (after subtracting already received yvOP rewards): $330,488.53

## Specification
### Overview
# [Proposal]: Partial Compensation for yvUSDT and yvDAI Vault Users Affected by Sonne Finance Exploit

### Rationale
TODO: Add Rationale.

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
TODO: List configurable values (if any) from the specification.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-79.md@@@
---
yip: 79
title: Multisig Compensation and Rotation
author: wavey
discussions-to: https://gov.yearn.fi/t/yip-79-multisig-compensation-and-rotation/14179
status: Proposed
created: 2024-09-26
---

## Simple Summary
Yearn's main multisig, [ychad.eth](https://etherscan.io/address/0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52), is a 6 of 9 multisig which has key powers within the protocol including ownership over the treasury. For more information, including the current list of signers, please refer to [the docs](https://docs.yearn.fi/developers/security/multisig).

## Abstract
Yearn's main multisig, [ychad.eth](https://etherscan.io/address/0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52), is a 6 of 9 multisig which has key powers within the protocol including ownership over the treasury. For more information, including the current list of signers, please refer to [the docs](https://docs.yearn.fi/developers/security/multisig).

This proposal aims to:
- outline a YFI compensation plan for signers
- rotate 3 multisig signers

## Motivation
TODO: Add Motivation.

## Specification
### Overview
### Proposal to rotate multisig signers and provide compensation

Yearn's main multisig, [ychad.eth](https://etherscan.io/address/0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52), is a 6 of 9 multisig which has key powers within the protocol including ownership over the treasury. For more information, including the current list of signers, please refer to [the docs](https://docs.yearn.fi/developers/security/multisig).

This proposal aims to:
- outline a YFI compensation plan for signers
- rotate 3 multisig signers

### Rationale
TODO: Add Rationale.

### Technical Specification
#### Compensation

Currently, ychad.eth signers earn no compensation. If passed, this proposal will:
- retroactively reward all current signers (including outgoing, excluding incoming) 1 YFI each to compensate for past efforts.
- reward all on-going signers (including incoming, excluding outgoing) with 1 YFI.

In summary, all signers who are part of both the past and present state will receive a transfer of 2 YFI. Signers who were part of only past or future state will receive a transfer of 1 YFI.

#### Signer Rotation

A transaction to rotate the first two signers will be queued to execute immediately upon passage of this proposal. Due to prior commitments, the final seat will be rotated at the start of December of this year.

replace the following outgoing signers:
| |                                   |
|--------|------------------------------------------|
| cp0x | `0x74630370197b4c4795bFEeF6645ee14F8cf8997D` |
| milkyklim   | `0x0Cec743b8CE4Ef8802cAc0e5df18a180ed8402A7`	 |
| **banteg  | `0x7A1057E6e9093DA9C1D4C1D049609B6889fC4c67` |

with the following incoming signers:
| |                                   |
|--------|------------------------------------------|
| cryptoharry (Inverse Finance)  | `0x962228a90eaC69238c7D1F216d80037e61eA9255` |
| michwill (Curve Finance)   | `0xFe45baf0F18c207152A807c1b05926583CFE2e4b` |
| **tapir (Yearn Finance)  | `0x700F1a984C962b447CcDb95c4c2D8074C65098a3` |

** *To be executed in December*

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-84.md@@@
---
yip: 84
title: Proposal to rotate multisig signer
author: wavey
discussions-to: https://gov.yearn.fi/t/yip-84-proposal-to-rotate-multisig-signer/14469
status: Proposed
created: 2025-04-13
---

## Simple Summary
If enacted, this proposal replaces multisig signer Monoloco with new signer Ephy and transfers 1 YFI to Ephy as compensation. Additionally, it will update active signer Lumberg's address to reflect a routine personal key rotation.

## Abstract
If enacted, this proposal replaces multisig signer Monoloco with new signer Ephy and transfers 1 YFI to Ephy as compensation. Additionally, it will update active signer Lumberg's address to reflect a routine personal key rotation.

## Motivation
### Background

Yearn's main multisig, [ychad.eth](https://etherscan.io/address/0xFEB4acf3df3cDEA7399794D0869ef76A6EfAff52), is a 6 of 9 multisig which has key powers within the protocol including ownership over the treasury. For more information, including the current list of signers, please refer to [the docs](https://docs.yearn.fi/developers/security/multisig).

As established in [YIP-79](https://gov.yearn.fi/t/yip-79-multisig-compensation-and-rotation/14179), signers who rotate on to the multisig shall receive 1 YFI compensation.

This rotation was initiated at the request of Monoloco, who has stepped back from active involvement in DeFi. We extend our gratitude to him for his contributions and dedicated service.

The proposed incoming signer is **Ephy**, Dewiz.xyz co-founder, a well-regarded contributor in the [Maker / Sky](https://forum.sky.money/u/0x3phemeralsoul/summary) ecosystem and a former MakerDAO Core Unit contributor. You can find more about Ephy on [X](https://x.com/0x3phemeralsoul) and [GitHub](https://github.com/0x3phemeralsoul).

## Specification
### Overview
If enacted, this proposal replaces multisig signer Monoloco with new signer Ephy and transfers 1 YFI to Ephy as compensation. Additionally, it will update active signer Lumberg's address to reflect a routine personal key rotation.

### Rationale
TODO: Add Rationale.

### Technical Specification
1. Replace the following signer:
    - outgoing: `0x1496546f89fc1605880e556c9a1d6c5e2409fb0a` (Monoloco)
    - incoming: `0x5Db9926c93085a92F14A85daBF6FF27b07362Cae` (Ephy)
2. Transfer 1 YFI from ychad.eth to Ephy's signer address.
3. Rotate Lumberg's key:
    - outgoing: `0x7321ED86B0Eb914b789D6A4CcBDd3bB10f367153` (Lumberg old)
    - incoming: `0xeA6c0837fef621E77329f85820F503cA09f2B3a9` (Lumberg new)

### Test Cases
Not applicable.

### Configurable Values
TODO: List configurable values (if any) from the specification.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
@@@yip-88.md@@@
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
