---
yip: 75
title: Launch V3
author: V3 Protocol Team & V3 "Secret Admirers" Group
discussions-to: https://gov.yearn.fi/t/yip-75-launch-v3/13591
status: Voting
created: 2023-08-15
---

## Simple Summary
Launch Yearn V3 by ratifying the deployed contracts, configuration parameters, and rollout plan for permissionless vaults and strategies.

## Abstract
This proposal approves the Yearn V3 design and launch plan. V3 standardizes vaults and strategies around ERC-4626, introduces roles and periphery contracts for flexible management, and adds protocol fee mechanics to capture revenue while enabling permissionless deployment.

## Motivation
V3 is intended to be a major upgrade over V2: more decentralized, easier for strategists to build, and more composable with DeFi. The goal is an open marketplace of vaults and strategies that broadens Yearn adoption and revenue capture.

## Specification
### Overview
- V3 vaults and strategies are ERC-4626 compliant.
- Vaults manage debt allocation across strategies; strategies can accept capital from multiple vaults.
- Tokenized Strategy templates simplify strategy development.

### Rationale
- ERC-4626 standardization increases composability and reduces custom integration work.
- Roles and periphery contracts enable decentralized management without compromising base security.
- Protocol fees ensure Yearn captures revenue even when third parties manage vaults/strategies.

### Technical Specification
1) Deployed contracts (release 3.0.0)
- Vault Blueprint (EIP-5202): 0xfC49ca826f8C68c0345410fcA0c7d1e0550d9ee9
- VaultFactory: 0xD1736eBbdefae37503F3eD8D718b61a494F24c1D
- TokenizedStrategy: 0xAE69a93945133c00B9985D9361A1cd882d107622
- Deployed on Ethereum mainnet, Polygon, Optimism, and Avalanche.

2) VaultFactory configuration
- MAX_FEE_BPS (constant): 50%.
- Default protocol fee: 20%.
- Protocol fee recipient: chain-specific V3/Treasury splitter.
- Governance: yChad or equivalent.
- Mainnet V3 vaults with V2 equivalents: custom protocol fee set at 40% of default.

3) Tokenized Strategy configuration
- MIN_FEE (constant): 5%.
- MAX_FEE (constant): 50%.

4) Fee model
- Fees can be charged at both vault and strategy layers.
- Protocol fee is applied as a percentage of total fees.

5) Rollout plan
- Initial public push on Polygon, then Arbitrum, Avalanche, Optimism, and Ethereum.
- VaultFactory governance to migrate to veYFI where applicable.

### Test Cases
Not applicable; this proposal ratifies deployed contracts and specifications.

### Configurable Values
- Protocol fee percentage and recipient.
- Governance for VaultFactory.
- Fee policies in external Accountant contracts.

## References
- https://github.com/yearn/yearn-vaults-v3
- https://github.com/yearn/tokenized-strategy
- https://github.com/yearn/vault-periphery
- https://github.com/yearn/tokenized-strategy-periphery
- https://github.com/Schlagonia/Yearn-ERC4626-Router
