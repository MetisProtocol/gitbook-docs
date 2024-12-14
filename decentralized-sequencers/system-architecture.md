---
description: >-
  The architecture of the Metis Decentralized Sequencer system is designed to
  achieve full decentralization and security for the Layer 2 network.
---

# System Architecture

[Overview](system-architecture.md#overview)

[System Architecture](system-architecture.md#system-architecture)

[Transaction Workflow](system-architecture.md#transaction-flow)

[How to Become a Sequencer](system-architecture.md#how-to-become-a-sequencer)

[Technical Requirements](system-architecture.md#technical-requirements)

Tokenomics

## **Overview**

The Metis Decentralized Sequencer architecture is designed to provide a fully decentralized, secure, and scalable solution for the Layer 2 (L2) network. By introducing a decentralized sequencer pool, Metis eliminates the risks associated with centralized systems, such as single points of failure, while ensuring fair participation and fault tolerance.

The system operates with seamless coordination between sequencers, validators, and block producers, leveraging decentralized infrastructure and community governance.

### **Key Features**

1. **Decentralization:**\
   Every network role is distributed, ensuring fairness and security.
2. **Fault Tolerance:**\
   Automatic rotation and reselection of sequencers in the event of failures or malicious activity.
3. **Efficiency and Scalability:**\
   Transactions are processed in batches for optimized throughput, while finalization happens on Ethereum Layer 1 (L1).
4. **Transparency and Governance:**\
   Governed by community voting power based on METIS token staking.

This document provides a detailed breakdown of the system components, workflows, governance mechanisms, technical requirements, and participation processes.

***

## **System Architecture**

The architecture of the Metis Decentralized Sequencer system is designed to achieve full decentralization, fault tolerance, and scalability for the Layer 2 network. It integrates three key layers that coordinate to ensure efficient transaction processing and secure block production.

### **Core Components**

1. **Ethereum Layer (L1):**
   * [**Smart Contracts**](smart-contract-natspec/)**:**\
     Responsible for locking METIS tokens, managing sequencer staking, and storing critical data for sequencer rotation.
   * **Finality:**\
     Provides security and finality by anchoring transaction batches on Ethereum.
2. **Consensus Layer (PoS):**
   * **Tendermint-based Nodes:**\
     Handles consensus on sequencer rotation and election processes.
   * **MPC (Multi-Party Computation):**\
     Enables secure and decentralized batch signing by sequencer nodes.
3. **Metis Layer (L2):**
   * **Sequencer Nodes:**\
     Processes user transactions, assembles blocks, and submits them to Ethereum L1.
   * **Bridge & Adapter Module:**\
     Facilitates communication between the PoS layer and the Metis layer. It ensures synchronization and updates sequencer information.

### **Workflow Summary**

1. **Transaction Processing:**
   * Users send transactions to the Metis RPC nodes.
   * The current sequencer validates, assembles, and executes the transactions.
2. **Batch Submission:**
   * The sequencer forms transaction batches and signs them through MPC.
   * Signed batches are submitted to Ethereum Layer 1 for finality.
3. **Sequencer Rotation:**
   * The PoS layer manages periodic sequencer rotations using a weighted random algorithm.
   * The active sequencer is replaced according to the staking weights, ensuring fairness and fault tolerance.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcO6NA7KavPeas0eZ_PV6moLn8be2GHPdez4ZYNrRSEgLAvHVGHVGRojprexeJz2QVw_2HyK3wkpxYaQUv2vr3EJGDbKRbW_xhwBhZcrxqykIYvGdTt63F1v7XyLwfXrSZv5-XFkadd2yDyDIslajNgMH1c?key=Cje97gPBg9LhrtdYWl-nMA)

### **Key Features of the Architecture**

* **Fair Sequencer Rotation:**\
  Sequencer rotation is controlled by staking weights and governed by community consensus.\
  Each sequencer's participation is validated through smart contracts on the Ethereum Layer.
* **Fault Tolerance and Recovery:**\
  If a sequencer fails or acts maliciously, the PoS layer reselects a new sequencer to maintain uninterrupted block production.
* **Transparent Operations:**\
  Sequencer rotations, staking data, and governance votes are fully transparent and auditable on-chain.
* **Security and Finality:**\
  By anchoring transaction batches to Ethereum, the system ensures robust security and immutable finality.

### Metis Nodes:

\\

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcKHyb8TMmUeiYkaw6E_nvpGsubgG-vjvLP38RhHVXTZRszEIv5v8Gws5i18NwO5eNdbGh999mZIrx64hIsrPE7uFTjKsoijCFJ06MFj2bjlsThEMRdObM2lcoRNOSsRLho5XahIjVq7jH3iZSimO2wCgHs?key=Cje97gPBg9LhrtdYWl-nMA" alt=""><figcaption></figcaption></figure>

Works on 3 layers (LockingPool.sol)

* **Ethereum layer:**
  * A set of smart contracts on the Ethereum network responsible for locking and rewards for sequencers.\\
* **Consensus (PoS) layer:**
  * A set of PoS Nodes based on Tendermint
  * When started, it detects the MPC addresses and calls the MPC module (see below) to trigger the keys generation if they do not exist;
  * When the sequencer submits L2BatchTxs to L1, the signature needs to be generated by multiple existing sequencers (more than 2/3 of the Sequencer nodes participate in MPC signing);
  * When the new sequencer node joins or exits, it performs the MPC resharing of private key shards without updating the mpc address in the locking contract (the mpc address can also be generated if needed);
  * Provides a variety of data query interfaces for Metis layer;
* **Metis layer:**
  * On this layer, for every new epoch another entity called sequencer is getting selected and/or rotated according to the information generated by the consensus layer;

***

## **Transaction Flow**

The transaction flow within the Metis Decentralized Sequencer system ensures efficient, secure, and decentralized processing. The flow is designed to handle transactions from users and produce finalized blocks on Layer 1 (Ethereum) with fault tolerance and scalability.

**Step-by-Step Transaction Flow**

1. **User Transaction Submission:**
   * Users interact with Metis dApps or wallets to send transactions via an RPC interface.
   * The transaction is received and validated by the current sequencer node.
2. **Transaction Validation and Inclusion:**
   * The sequencer checks the validity of the transaction, ensuring it adheres to protocol rules.
   * Valid transactions are assembled into a block for Layer 2.
3. **Block Execution and Confirmation:**
   * The sequencer node executes the transactions in the block.
   * A transaction hash and block number are returned to the user as confirmation.
4. **Batch Formation:**
   * The sequencer groups multiple Layer 2 blocks into a single batch.
   * This batch contains Merkle proofs for all transactions, ensuring tamper-proof validation.
5. **Multi-Party Computation (MPC) Signature:**
   * The batch is signed using an MPC mechanism, requiring signatures from a majority of active sequencers.
   * This process ensures decentralization and security for the batch submission.
6. **Batch Submission to Ethereum (L1):**
   * The signed batch is submitted to the Ethereum Layer 1 via the **Bridge & Adapter module**.
   * This ensures the finality of transactions by anchoring them on Ethereum.
7. **Sequencer Rotation (if applicable):**
   * At periodic intervals or upon fault detection, the PoS layer rotates the sequencer role to a new node.
   * The new sequencer takes over transaction processing seamlessly.

***

## **How to Become a Sequencer**

The process of becoming a sequencer in the Metis Decentralized Sequencer system is essential for contributing to the network's decentralization and earning rewards. It involves meeting technical requirements, locking METIS tokens, and maintaining operational reliability.

For a detailed, step-by-step guide on becoming a sequencer, including prerequisites, application process, and governance mechanisms, visit the dedicated page:

\
👉 [**How to Become a Sequencer**](how-to-become-a-sequencer/)

***

## **Technical Requirements**

**System Specifications**:

|         |          |
| ------- | -------- |
| CPU     | 16-core  |
| RAM     | 32 GB    |
| STORAGE | 1 TB SSD |

**Network Configuration**: Please ensure these ports are exposed for P2P connection. Refer to [metis-node](https://github.com/MetisProtocol/metis-charts/blob/main/charts/metis-node/README.md) for the details.

***
