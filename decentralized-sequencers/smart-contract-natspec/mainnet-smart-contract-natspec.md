# Mainnet Smart Contract (natSpec)

All activities related to **locking**, **rewards**, and **additional locking operations** for Sequencers are executed on the **Ethereum L1 mainnet (chainid: 1)**. These smart contracts form the backbone of Sequencer lifecycle management, enabling seamless integration into the Metis ecosystem.

***

#### **Key Contracts**

The following contracts are critical for Sequencer operations:

| **Contract**    | **Address**                                  |
| --------------- | -------------------------------------------- |
| **LockingInfo** | `0x0fe382b74c3894b65c10e5c12ae60bbd8faf5b48` |
| **LockingPool** | `0xd54c868362c2098e0e46f12e7d924c6a332952dd` |

Sequencers can interact directly with these contracts to manage rewards, lock-ups, and related activities without requiring frontend tools.

***

#### **Sequencer Lifecycle: Step-by-Step Guide**

1. **Review Technical Documentation**\
   Thoroughly review all technical documentation to understand the operational and technical requirements for running a Sequencer.
2. **Apply for Whitelist**\
   Submit an application to join the Sequencer whitelist, which is required to begin operations.
3. **Set Up and Run Your Sequencer**\
   Deploy your Sequencer node, configure it correctly, and securely back up your private keys. Detailed setup instructions are available in the README.md file.
4. **Submit Sequencer Information**\
   Provide your Sequencer details via a pull request to the **GitHub repository**. This should include:
   * **name**: Your Sequencer's name.
   * **avatar**: URL for your Sequencer's logo or avatar.
   * **url**: Website or social profile link (must start with `https://`).
   * **address**: Whitelist address for Sequencer lock-up.
   * **seq\_addr**: Sequencer address generated by the node.
   * **pubkey**: Uncompressed public key generated by your server (ensure to remove any extra `04` characters).
   * **desc**: A brief description of your organization or individual setup.
5. **Approve Locking Tokens**\
   Approve the desired amount of METIS tokens to be locked using the `LockingInfo` contract as the spender.
6. **Lock METIS Tokens**\
   Use the **LockPool contract** to lock METIS tokens by calling either the `lockFor` or `lockWithRewardRecipient`method, depending on whether you are assigning a reward recipient.
7. **Check Sequencer Status**\
   Use the `sequencers` method in the **LockingPool contract** to verify your Sequencer's status and rewards.
8. **Claim Mining Rewards**\
   Retrieve accrued mining rewards using the `withdrawRewards` method. If you have not assigned a reward recipient, use the `setSequencerRewardRecipient` method to configure one before claiming rewards.

***

#### **Contract Functionalities**

The **LockingPool contract** provides key methods to efficiently manage Sequencer operations, including querying status, locking tokens, and handling rewards.

***

**Reading Contract Information**

1. **`seqOwners`**\
   Retrieves comprehensive Sequencer status using the owner's address.
   * **Parameter**: `seqId (uint256)` - The Sequencer ID.
   * **Response**: Returns details of the Sequencer's operational state.
2. **`seqSigners`**\
   Retrieves Sequencer information using the signer's address.
   * **Parameter**: `seqId (uint256)` - The Sequencer ID.
   * **Response**: Returns details of the Sequencer's operational state.
3. **`sequencers`**\
   Accesses all detailed information about a Sequencer using its ID.
   * **Parameter**: `seqId (uint256)` - The Sequencer ID.
   *   **Response**:

       ```python
       amount (uint256): Locked METIS tokens.
       reward (uint256): Accrued rewards.
       activationBatch (uint256): Activation batch number.
       updatedBatch (uint256): Last updated batch number.
       deactivationBatch (uint256): Deactivation batch number.
       deactivationTime (uint256): Time of deactivation.
       unlockClaimTime (uint256): Time for claiming unlocked tokens.
       nonce (uint256): Nonce value.
       owner (address): Owner's address.
       signer (address): Signer's address.
       pubkey (bytes): Signer's public key.
       rewardRecipient (address): Reward distribution address.
       status (uint8): Current Sequencer status.
       ```

***

**Writing Contract Information**

1. **`lockFor`**\
   Locks METIS tokens and assigns Sequencer ownership.
   * **Parameters**:
     * `_signer (address)`: Sequencer signer address.
     * `_amount (uint256)`: Amount of METIS tokens to lock.
     * `_signerPubkey (bytes)`: Uncompressed public key of the signer.
2. **`lockWithRewardRecipient`**\
   Similar to `lockFor`, but includes an additional parameter to specify a reward recipient.
   * **Parameters**:
     * `_signer (address)`: Sequencer signer address.
     * `_rewardRecipient (address)`: Reward recipient address.
     * `_amount (uint256)`: Amount of METIS tokens to lock.
     * `_signerPubkey (bytes)`: Uncompressed public key.
3. **`relock`**\
   Adds more tokens to an existing lock or locks accrued rewards.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_amount (uint256)`: Additional tokens to lock (can be `0` if relocking rewards).
     * `_lockReward (bool)`: Whether to lock current rewards.
4. **`setSequencerRewardRecipient`**\
   Updates or assigns a reward recipient address.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_recipient (address)`: New reward recipient address.
5. **`withdrawRewards`**\
   Withdraws accrued rewards to the specified address.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit for the operation.
6. **`unlock`**\
   Initiates the unlocking process for METIS tokens.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit for the bridge operation.
7. **`unlockClaim`**\
   Claims unlocked tokens after the mandatory 21-day waiting period.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit.
8. **`withdraw`**\
   Partially withdraws locked tokens while maintaining the minimum lock balance.
   * **Parameters**:
     * `_amount (uint256)`: Amount to withdraw.
     * `_seqId (uint256)`: Sequencer ID.

***

#### **Best Practices**

* Always verify recipient addresses before submitting transactions, especially for rewards or withdrawals.
* Securely manage and back up private keys for long-term Sequencer integrity.
* Monitor gas parameters closely to avoid transaction failures.
