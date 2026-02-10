---
yip: 84
title: Proposal to rotate multisig signer
author: wavey
discussions-to: https://gov.yearn.fi/t/yip-84-proposal-to-rotate-multisig-signer/14469
status: Proposed
created: 2025-04-13
---

## Simple Summary
Rotate one ychad.eth signer, update Lumberg's signer address, and pay 1 YFI to the incoming signer.

## Abstract
This proposal replaces Monoloco with Ephy as a ychad.eth signer, updates Lumberg's key, and pays 1 YFI compensation to the incoming signer.

## Motivation
Signer rotation keeps the multisig current and maintains accountability for signer service.

## Specification
### Overview
- Replace Monoloco with Ephy.
- Rotate Lumberg's signer key.
- Transfer 1 YFI to Ephy.

### Rationale
- Rotations are part of ongoing multisig maintenance and compensation policy (YIP-79).

### Technical Specification
1) Replace signer
- Outgoing: 0x1496546f89fc1605880e556c9a1d6c5e2409fb0a (Monoloco)
- Incoming: 0x5Db9926c93085a92F14A85daBF6FF27b07362Cae (Ephy)

2) Compensation
- Transfer 1 YFI from ychad.eth to Ephy's signer address.

3) Lumberg key rotation
- Outgoing: 0x7321ED86B0Eb914b789D6A4CcBDd3bB10f367153
- Incoming: 0xeA6c0837fef621E77329f85820F503cA09f2B3a9

### Test Cases
Not applicable.

### Configurable Values
- Compensation amount.

## References
- https://gov.yearn.fi/t/yip-84-proposal-to-rotate-multisig-signer/14469
