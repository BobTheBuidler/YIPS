---
yip: 79
title: Multisig Compensation and Rotation
author: wavey
discussions-to: https://gov.yearn.fi/t/yip-79-multisig-compensation-and-rotation/14179
status: Voting
created: 2024-09-26
---

## Simple Summary
Rotate three ychad.eth multisig signers and introduce a YFI compensation policy for multisig service.

## Abstract
This proposal updates the ychad.eth signer set and establishes a compensation structure: 1 YFI for past service and 1 YFI for ongoing service. It specifies outgoing and incoming signer addresses and timing.

## Motivation
Multisig signers hold critical protocol responsibilities and should be compensated for past and ongoing service. Rotation keeps signer set current.

## Specification
### Overview
- Rotate three signers on ychad.eth.
- Pay 1 YFI for past service and 1 YFI for ongoing service.

### Rationale
- Compensation aligns incentives and acknowledges operational risk.
- Rotation improves resilience and continuity.

### Technical Specification
1) Compensation
- Current signers (including outgoing, excluding incoming): 1 YFI each.
- Ongoing signers (including incoming, excluding outgoing): 1 YFI each.
- Signers present before and after rotation receive 2 YFI total.

2) Signer rotation
Outgoing:
- cp0x: 0x74630370197b4c4795bFEeF6645ee14F8cf8997D
- milkyklim: 0x0Cec743b8CE4Ef8802cAc0e5df18a180ed8402A7
- banteg: 0x7A1057E6e9093DA9C1D4C1D049609B6889fC4c67

Incoming:
- cryptoharry (Inverse Finance): 0x962228a90eaC69238c7D1F216d80037e61eA9255
- michwill (Curve Finance): 0xFe45baf0F18c207152A807c1b05926583CFE2e4b
- tapir (Yearn Finance): 0x700F1a984C962b447CcDb95c4c2D8074C65098a3

Timing:
- First two rotations execute immediately after passage.
- Final seat executes at the start of December (per proposal note).

### Test Cases
Not applicable.

### Configurable Values
- Compensation amount per signer.
- Rotation timing.

## References
- https://gov.yearn.fi/t/yip-79-multisig-compensation-and-rotation/14179
