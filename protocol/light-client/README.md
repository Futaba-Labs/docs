---
description: Light Client is a contract that verifies proof and extracts data
---

# Light Client

A contract that verifies the proof, and developers can define it on their own.

In the initial stage, a mock-up verification using Patricia Merkle Tree (MPT) is created for account proof and storage proof. Verification methods such as ZKP will be implemented in the future.

The Light Client Contract defines the `requestQuery` and `verify` functions as interfaces.

Also, since verification requires the acquisition of block headers (state root), the method of acquisition can be customized within this contraption at this time ([konoha](../konoha/ "mention")).
