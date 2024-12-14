---
description: Welcome to the Metis Decentralized Sequencer Operation Guide.
---

# Decentralized Sequencers

This document serves as a comprehensive resource to understand the principles, functionalities, and operations of sequencer nodes in the Metis Layer 2 network.

With the introduction of Decentralized Sequencers, Metis aims to achieve full decentralization of its Layer 2 networks, overcoming the limitations of traditional centralized sequencers. This system is designed to enhance security, scalability, and transparency while ensuring fault tolerance and efficient transaction ordering.

[Quick Intro](./#quick-introduction)

[System Architecture](system-architecture.md)

[How to Become a Sequencer](how-to-become-a-sequencer/)

[Sequencer operation](sequencer-operation/)

[Smart Contract (natspec)](smart-contract-natspec/)

[FAQs](faqs.md)

### **Quick Introduction**

#### **What are Decentralized Sequencers?**

Decentralized Sequencers are key entities within the Metis Layer 2 ecosystem, responsible for:

* Sequencing transactions and assembling blocks on the Metis Layer 2 chain.
* Submitting batched transactions to Ethereum Layer 1 for security and finality.
* Ensuring seamless rotation and fault tolerance through decentralized governance.

Unlike centralized systems, Metis leverages a pool of decentralized sequencers to distribute responsibilities and eliminate single points of failure. This model enhances the resilience of the network while fostering community-driven participation.\\

#### **Why Decentralized Sequencers?**

The transition to decentralized sequencers is a critical milestone for Metis. The primary objectives include:

1. **Resilience and Security**: Elimination of single points of failure by distributing the sequencing process across multiple nodes.
2. **Fair Participation**: Introducing a weighted voting mechanism based on staked METIS tokens, ensuring fairness in sequencer selection.
3. **Governance and Accountability**: Establishing governance mechanisms to penalize malicious behavior and reward contributors.
4. **Efficiency and Scalability**: Ensuring efficient transaction processing and block production across the Layer 2 network.

***

#### **Key Features of Decentralized Sequencers**

1. **Sequencer Rotation**
   * Ensures fair distribution of block production roles.
   * Utilizes a rotation mechanism managed by the Proof-of-Stake (PoS) consensus layer and smart contracts.
2. **Fault Tolerance**
   * Automatic reselection of sequencers in case of failure or malicious activity.
   * Guarantees network stability by replacing inactive or misbehaving sequencers.
3. **Community Governance**
   * Decentralized governance ensures community participation in decision-making.
   * Slashing mechanisms to penalize malicious behavior and reward honest participants.
4. **Transparency**
   * Publicly auditable sequencer operations and rotation records.
   * All sequencer-related actions are stored on-chain, ensuring transparency.
