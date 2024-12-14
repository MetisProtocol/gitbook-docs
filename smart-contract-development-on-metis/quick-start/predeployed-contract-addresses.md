# Predeployed Contract Addresses

The Metis protocol consists of several contracts that are deployed on some specific addresses. The contracts have been deployed on L2, L1, Andromeda, and Stardust testnet. You can use the etherscan explorer to see full details about deployed contract addresses. The [Metis Github page](https://github.com/MetisProtocol/mvm/tree/develop/packages/contracts/deployments) shows all the deployed contract addresses.

| **Network**                                             | **Andromeda (Mainnet)**                    | **Sepolia (Testnet)**                      |
| ------------------------------------------------------- | ------------------------------------------ | ------------------------------------------ |
| Chain ID                                                | 1088                                       | 59902                                      |
| BondManager[^1]                                         | 0x595801b85628ec6979C420988b8843A40F850528 | 0xE0cDbb071144489b52Af578BDdea84dBDFd85576 |
| CanonicalTransactionChain[^2]                           | 0x56a76bcC92361f6DF8D75476feD8843EdC70e1C9 | 0x5435d351e0aCc874579eC67Ba46440ee6AC892b8 |
| ChainStorageContainer-CTC-batches[^3]                   | 0x38473Feb3A6366757A249dB2cA4fBB2C663416B7 | 0x92F90779986C294A22DC43C8f6aE1F5d8B2728E4 |
| ChainStorageContainer-CTC-queue[^4]                     | 0xA91Ea6F5d1EDA8e6686639d6C88b309cF35D2E57 | 0x10A493fFAc17DCc6Ea70d8c3BD19160ea0d3822B |
| ChainStorageContainer-SCC-batches[^5]                   | 0x10739F09f6e62689c0aA8A1878816de9e166d6f9 | 0x185AB4701DBf521B44838fa72af99880730d5CE6 |
| L1StandardBridge\_for\_verification\_only[^6]           | 0x101500214981e7A5Ad2334D8404eaF365C2c3113 | 0xd41bc137120BFcEd907093741ea402631d7616BE |
| Lib\_AddressManager[^7]                                 | 0x918778e825747a892b17C66fe7D24C618262867d | 0xa66Fa1eD0f1C1ee300893B4eb5493FeAD9a7e9c3 |
| MVM\_CanonicalTransaction\_for\_verification\_only[^8]  | 0x431e877E216714647a4DCcEFFC03d7B4Fd4B825E | 0xFD98b95ad84f459697c29aFA75229e93F6D2B8A2 |
| MVM\_DiscountOracle[^9]                                 | 0xC8953ca384b4AdC8B1b11B030Afe2F05471664b0 | 0x4fd947DfF05a255F78E355C23c8B2E98bf029126 |
| MVM\_L2ChainManagerOnL1\_for\_verification\_only[^10]   | 0x9E2E3be85df5Ca63DE7674BA64ffD564075f3B48 | 0x8c52c668A23970759F21Cbc274fd63C8e4Bdfd4D |
| MVM\_StateCommitmentChain\_for\_verification\_only[^11] | 0x4549292213D41CB62E94e7E2DDC4b468a4CDD16d | 0xfaAd7fFe832775c66Fb3586f0AF3Ffc09B173ff2 |
| MVM\_Verifier[^12]                                      | 0x9Ed4739afd706122591E75F215208ecF522C0Fd3 |                                            |
| MVM\_Verifier\_for\_verification\_only[^13]             | 0xB2e2060A179e67cA4299Cc79fA337B98791DE069 | 0x88d98AfC2344F9554478C1CDf8062c7F32145176 |
| OVM\_L1CrossDomainMessenger[^14]                        | 0x8bF439ef7167023F009E24b21719Ca5f768Ecb36 | 0x22796245e27190cAFD7b50a93585f30f60a03f46 |
| Proxy\_\_MVM\_CanonicalTransaction                      | 0x6A1DB7d799FBA381F2a518cA859ED30cB8E1d41a | 0x6281F34652359cfBa1781D84DAb939f99aaa0e29 |
| Proxy\_\_MVM\_ChainManager                              | 0xf3d58D1794f2634d6649a978f2dc093898FEEBc0 | 0xEf3375Fc36007a585Ee6e73BF95797273f4F9b49 |
| Proxy\_\_MVM\_StateCommitmentChain                      | 0xA2FaAAC9120c1Ff75814F0c6DdB119496a12eEA6 | 0x9DCC53737FcB3E86a17CF435ca3c15390D4FC7Ed |
| Proxy\_\_MVM\_Verifier                                  | 0xe70DD4dE81D282B3fa92A6700FEE8339d2d9b5cb | 0x1B9B31E637278c207991F6e96074928728359A10 |
| Proxy\_\_OVM\_L1CrossDomainMessenger                    | 0x081D1101855bD523bA69A9794e0217F0DB6323ff | 0x4542c621eEe9fC533c2e6bd80880C89990EE10cD |
| Proxy\_\_OVM\_L1StandardBridge                          | 0x3980c9ed79d2c191A89E02Fa3529C60eD6e9c04b | 0x9848dE505e6Aa301cEecfCf23A0a150140fc996e |
| StateCommitmentChain[^15]                               | 0xf209815E595Cdf3ed0aAF9665b1772e608AB9380 | 0xA059B3307f534943Ee6c710D9582B42543847Eb1 |

[^1]: **BondManager** is a component responsible for managing and maintaining bonds or collateral deposits that are used to secure the network.

[^2]: The **CanonicalTransactionChain** is essentially the ordered list of transactions that have been submitted to the Layer 2 chain. It serves as the official record of all transactions that have been processed and included in the chain.

[^3]: The **ChainStorageContainer-CTC-batches** is a data structure that holds batches of transactions which are part of the CanonicalTransactionChain in Layer 2 solutions like Optimistic Rollups.

[^4]: The **ChainStorageContainer-CTC-queue** is a data structure designed to manage and temporarily store transactions that are waiting to be included in the next batch of the CanonicalTransactionChain (CTC).

[^5]: The **ChainStorageContainer-SCC-batches** is a data structure that holds batches of state commitments within a state commitment chain (SCC). These commitments represent the state of the Layer 2 chain at various points in time.

[^6]: The **L1StandardBridge** is a smart contract deployed on Layer 1 (Ethereum mainnet) that handles the transfer of assets (such as ETH and ERC20 tokens) and messages between Layer 1 and Layer 2. The "**for verification only**" aspect indicates that this bridge is also responsible for verifying the correctness of state transitions and transactions that occur on Layer 2.

[^7]: The **Lib\_AddressManager** is a smart contract utility that serves as a registry for storing and managing addresses of key contracts and components in a Layer 2 solution. This central address management helps ensure that all components can easily locate and interact with each other.

[^8]: The **MVM\_CanonicalTransaction\_for\_verification\_only** is a specialized component or function designed to handle the verification of transactions within a CanonicalTransactionChain. This component ensures that transactions are valid and adhere to the rules and protocols established by the Layer 2 (L2) solution.

[^9]: The **MVM\_DiscountOracle** is a service or smart contract that provides information about discounts or reduced transaction fees within the MetaMask Virtual Machine (MVM) or another blockchain-based ecosystem. This oracle supplies data that can be used to adjust the cost of operations dynamically.

[^10]: The **MVM\_L2ChainManagerOnL1\_for\_verification\_only** is a smart contract or a set of smart contracts on the Ethereum mainnet (Layer 1) that manages and verifies the state and transactions of the Layer 2 chain. This component is focused solely on verification tasks to ensure the integrity and correctness of the L2 chain from the L1 perspective.

[^11]: The **MVM\_StateCommitmentChain\_for\_verification\_only** is a specialized module or smart contract that manages and verifies state commitments on the Metis Layer 2 (L2) chain. It is responsible for recording cryptographic commitments to the state of the L2 chain and ensuring these commitments are valid and secure.

[^12]: The **MVM\_Verifier** is a smart contract or a module within the Metis Virtual Machine (MVM) dedicated to verifying the accuracy and integrity of transactions, state transitions, and other operations within the Layer 2 (L2) chain.

[^13]: The **MVM\_Verifier\_for\_verification\_only** is a component within the Metis Virtual Machine that exclusively handles the verification of transactions and state transitions. Its purpose is to ensure the validity and integrity of these operations, playing a crucial role in the security and reliability of the Metis Layer 2 chain.

[^14]: The **OVM\_L1CrossDomainMessenger** is a smart contract deployed on the Ethereum mainnet (L1) that handles the sending and receiving of messages between Layer 1 and Layer 2. This component is essential for enabling cross-domain interactions, allowing contracts and users on L1 to communicate with contracts and users on L2.

[^15]: The **SCC contract** is a smart contract deployed on the L1 blockchain that records and manages cryptographic commitments to the state of the L2 chain. It plays a vital role in anchoring the L2 state to L1, ensuring security and verifiability.
