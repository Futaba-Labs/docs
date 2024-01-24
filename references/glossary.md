---
description: Terms used in Futaba
---

# Glossary

#### Src chain

The source chain requests data and receives the result.

#### Destination chain

The chain from where data is requested and the query is executed through the Relayer and returned to the Src chain.

#### User Contract

A contract is defined by the developer, which is the calling source of the Gateway API.

#### Gateway Contract

The contract endpoint requests data acquisition.

#### Light Client Contract

A contract that verifies data and can build its logic.

#### Relayer

An intermediary between the src chain and the destination chain, which acquires proof for the destination chain and sends the data to the src chain.

#### Storage proof

A cryptographic commitment is used to prove that a storage value or transaction has been committed to the blockchain tree and that it is valid.

#### Konoha

A module for retrieving the appropriate block header for each ecosystem. The default is Chainlink Oracle, with the possibility of using ZK Coprocessors such as Largange or Herodotus in the future.
