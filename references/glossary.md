---
description: Terms used in Futaba
---

# Glossary

#### Src chain

The source chain which requests data and receives the result.

#### Destination chain

The chain from where data is requested and the query is executed through the Relayer and returned to the Src chain.

#### User Contract

A contract is defined by the developer, which is the calling source of the Gateway API.

#### Gateway Contract

The contract endpoint requests data acquisition.

#### Light Client Contract

A contract that verifies data and can build its own logic.

#### Oracle Contract

A contract that requests Oracle and defines its callback function.

#### Relayer

An intermediary between the src chain and the destination chain, which acquires proof for the destination chain and sends the data to the src chain.

#### Oracle

A node used to obtain the height block header of a specific block on a specific chain.
