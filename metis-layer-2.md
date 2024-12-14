# Metis Layer 2

The Metis Layer 2 solution is an innovative, Ethereum-compatible rollup designed to provide scalability, lower transaction costs, and enhanced decentralization. By leveraging cutting-edge technologies like Optimistic Rollups, ZKP, Decentralized Sequencers, and off-chain storage, Metis empowers developers to build scalable Web3 applications.

This document provides a detailed explanation of how Metis Layer 2 functions, focusing on five key areas:

1. [**Common Questions** ](metis-layer-2.md#id-1.-common-questions)– Simplified answers to the most frequent questions about Metis Layer 2.
2. [**Structure** ](metis-layer-2.md#id-2.-structure)– A breakdown of the key components and processes that make Metis Layer 2 work.
3. [**Transaction Processing Algorithm** ](metis-layer-2.md#id-3.-transaction-processing-algorithm)– A step-by-step guide to how transactions are handled.
4. [**Special Scenarios** ](metis-layer-2.md#id-4.-special-scenarios)– How Metis handles unique and uncommon situations.
5. [**Visual Diagrams** ](metis-layer-2.md#id-5.-diagrams)– Illustrations to help visualize the Metis Layer 2 architecture.

## 1. Common Questions

* **What is Metis L2?**\
  Metis is an Ethereum Layer 2 leveraging innovative technologies such as Optimistic Rollup, ZKP, Decentralized Sequencers, off-chain storage, etc. for empowering a sustainable Web3 economy.
* **Why is Metis better than other L2s?**\
  Tech-wise, Metis is designed in a way that prevents single-point-of-failure issues. That means when you turn off some part of the system, the entire structure will not stop or lose its security. This way Metis solves a problem that other L2 solutions suffer from (see Arbitrum going down in the winter of 2022 because of such issues).
* **How does Metis maintain a constant uptime?**\
  The system is designed in a way that any malfunctioning actor gets charged and swapped out through the constant cycles of rotation. It is accomplished with the Peer Network which includes Sequencers, Verifiers, and Consensus (PoS) layer. After the next major upgrade, there will be no more downtime at all, and the maintenance schedule will be controlled by the community through the governance protocol.
* **What is the Peer Network?**\
  It is a network of decentralized actors (nodes) that serve the Metis system. Anyone can become a part of the Peer Network just by setting up a node on their computer. The participants of the Peer Network receive revenue with a portion of the fees from all the transactions that go through the Peer Network.
* **How does Metis achieve cheaper transactions?**\
  Metis utilizes the Merkle Tree State and Batch Roots (MTSR/MTTBR). In an oversimplified analogy, you can think about MTSR or MTTBR as a bank cheque that you can withdraw the money from. Let’s say you want to give someone a big sum of money: in a more efficient way you would give a bank cheque instead of a bag of cash. Metis does the same: instead of posting huge chunks of transaction data to Layer 1, Metis utilizes MTSR/MTTBR to make it way more efficient while still utilizing the security of Ethereum.
* **What is Merkle Tree State Root / Merkle Tree Transaction Batch Root (MTSR/MTTBR)?**\
  It is a hashing algorithm which is aimed to identify the inconsistencies between the nodes (or participants of the Peer Network in our case). Merkle tree is created by dividing data into many pieces, which are then hashed repeatedly to form the Merkle Tree Root. You can efficiently verify if something has gone wrong with a piece of data.
* **Does Metis still provide Ethereum Layer 1 security by using the Merkle Tree algorithm?**\
  Yes, you can practically check whether your transaction is included into a MTSR/MTTBR data batch (that’s also how Metis solves the data availability problem), and it cannot be maliciously altered without your private keys. Ethereum Layer 1 processes the transaction data, Metis instead utilizes Ethereum Layer 1 to process MTSR/MTTBR batches which were derived from the transaction data.
* **What will happen with my money if I send a transaction and the blockchain gets stopped?**\
  Your money will either successfully reach the desired destination address, or you will have to resend the transaction. No money will be lost.
* **Where does Metis store the transaction data?**\
  Metis stores the transaction data in **Memolabs** storage, which is based on blockchain technology to provide safe, efficient, and large-scale decentralized cloud storage services.
* **If Memolabs goes down, will the system still operate?**\
  Yes, in this case the Verifier downloads the transaction data from the blockchain. If the blockchain is unavailable, then Verifier requests Sequencer to post the transaction data on L1 and then downloads it from there. You can check these cases in diagrams or algorithm section below for more details.

## 2. Structure

The entire structure of Metis Layer 2 is designed around several algorithm loops which are designated to mitigate the potential damage and filter the possible malfunctions of decentralized actors and/or other outer ill-wishers.

There are 7 distinguished actors participating in the system (Governance Protocol is a part of L1 / Smart contract, but it handles a number of functions that make it a separate entity):

1. **User** sends the transactions;
2. **Sequencer Node** (it’s a part of a decentralized network with rotations, etc.) is responsible for correcting the blockchain, propagating the blocks through the Peer Network;
3. **Metis Blockchain** is an entity held by Decentralized Sequencer;
4. **Verifier** (decentralized entity) is the counterpart of Sequencer, mostly responsible for keeping an eye on the Sequencer to not provide false/invalid data;
5. **L1 Smart Contracts** — the set of smart contracts that handle the security of the system, solve the disputes between Sequencer and Verifier;
6. **Memolabs** (decentralized entity) stores the transaction data;
7. **The Governance Protocol** is responsible for anything related to the efficiency of the system.

## 3. Transaction Processing Algorithm

## 4. Special Scenarios

Describing the extraordinary cases and how the Metis system handles them.

1. **What is the "Insecure transaction state of the system"?** It is a special state when the system stops in some sense because the security of transactions after the problematic batch cannot be guaranteed. The system enters an insecure transaction state for the data availability request time window until the next rotation. During this time window, if the Sequencer provides valid data, the system will exit the insecure transaction state. For now, the duration of the data availability request time window is 24 hours.
2. **What if the Sequencers unite to stop the system?** The system will only halt if more than 1/3 of Sequencers stop producing blocks for the Metis blockchain. In the event of a single node failure, it will rotate to the next Sequencer after a 1-minute timeout period. The community has proposed governance measures to penalize problematic or malicious Sequencers. For more details, see \[this page].
3. **What if the Sequencer forged both transaction data and the batch?** Nothing to worry about; a Sequencer that alters transactions will not be able to pass verification by other Sequencers.
4. **What if the Sequencer sends forged data to Memolabs and L1 / Smart Contract?** The Sequencer is not authorized to perform this action.

## 5. Diagrams

Visual diagrams and flowcharts are provided to illustrate key processes and components within Metis Layer 2. These diagrams offer a comprehensive overview of how transactions flow through the system, sequencer rotations, and the Peer Network’s role.

{% embed url="https://3834785237-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FMkexAWdCekeDPPCMOdGs%2Fuploads%2FaqGw2wijGQC8hJ9PjFFd%2FTransaction%20Flowchart%204_14_2024.drawio.png?alt=media&token=03843f73-050f-4f2e-839f-1ef910c7abb7" %}
Transaction Flowchart
{% endembed %}

{% embed url="https://3834785237-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FMkexAWdCekeDPPCMOdGs%2Fuploads%2FJOfaPDB3p1PhH3DFMw1k%2FTransaction%20Flowchart%204_14_2024.drawio%20(1).png?alt=media&token=fd43de0f-6b64-4b4e-bc04-e405556efd3e" %}
Simple Transaction Flowchart
{% endembed %}

{% embed url="https://3834785237-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FMkexAWdCekeDPPCMOdGs%2Fuploads%2Fs4wCDGdAwzIHz9HMyX8M%2FTransaction%20Flowchart%204_14_2024.drawio%20(2).png?alt=media&token=ac37ae58-55a5-4117-99e7-00fea808ac74" %}
Deposit Flowchart
{% endembed %}
