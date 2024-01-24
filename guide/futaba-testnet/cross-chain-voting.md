---
description: Utilize assets from other chains as voting rights
---

# Cross-chain voting

In the Futaba demo, Cross-chain voting involves using Ethereum's NFTs as voting rights, while the actual voting process takes place on Layer 2. Here are the steps:

1. Send a voting transaction to Mumbai to initiate the voting process.
2. Utilize Futaba to confirm whether the Ethereum NFT is valid.
3. Execute the voting process in the response transaction.

This process allows you to leverage Ethereum's NFTs for voting within the Futaba ecosystem while conducting the actual voting on a Layer 2 solution for scalability and cost efficiency.

To use this feature, three steps are required: minting NFTs, creating proposals, and executing votes.

#### 1. Mint voting NFT

First, let's mint a sample NFT. Please mint it from [Faucet](https://demo.futaba.dev/faucet).

Please make a note of the block height of the minted transaction here. You will need it when creating a proposal.

#### 2. Create a proposal

Next, let's create a proposal. Click the "Create proposal" button to access the creation page.

In the form, you will need to input the following information: Title, Expiration date, Block height, and Description. Regarding the block height, you should set it to a value greater than the block height of the transaction where the NFT was minted. This will confirm that you possess the NFT.

Once you have completed the input, press the "Create" button to submit the transaction. After the transaction is completed, you will see the proposal listed on the proposal overview page.

<figure><img src="../../.gitbook/assets/create_proposal" alt=""><figcaption></figcaption></figure>

#### 3. Voting

When you click on the proposal you created earlier, you will see the details of the proposal.

<figure><img src="../../.gitbook/assets/show_proposal" alt=""><figcaption></figcaption></figure>

There, you can vote "Yes" or "No." You can check the status of the voting transaction in the Explorer.

<figure><img src="../../.gitbook/assets/voting" alt=""><figcaption></figcaption></figure>

After voting is complete, when you revisit the proposal details, you will be able to confirm that your vote has been recorded.

<figure><img src="../../.gitbook/assets/voting_result" alt=""><figcaption></figcaption></figure>

