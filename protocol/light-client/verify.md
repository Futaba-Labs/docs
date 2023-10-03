---
description: Function to verify proof
---

# Verify

This function uses Merkle Patricia Trie (MPT) to verify the proof.

```solidity
function verify(
    bytes memory message
) public returns (bool, bytes[] memory);
```

<table><thead><tr><th width="133.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>message</code></td><td>Data encoded with proof information (You can get an array of <code>Proof</code> when you decode)</td></tr></tbody></table>

What the `verify` function does:

* Verify account proof using MPT to obtain the target storage hash
* Verify the storage proof using MPT to obtain the value of the target storage slot

{% hint style="info" %}
This validation is used in the initial phase and other validation methods may be developed as modules in the future, such as the use of zkp.
{% endhint %}
