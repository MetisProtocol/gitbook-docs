# Testnet Smart Contract (natSpec)

All locking, reward distribution, and additional locking operations for Sequencers are executed on the **Sepolia Testnet**. These contracts are integral to managing the Sequencer lifecycle and ensuring smooth participation in the network.

**Key Contracts**

The following contracts are essential for Sequencer operations:

| **Contract**    | **Address**                                  |
| --------------- | -------------------------------------------- |
| **LockingInfo** | `0x390A6fE63385522E87e248BC5200f7d3a02F994b` |
| **LockingPool** | `0x7591940125cC0344a65D60319d1ADcD463B2D4c3` |

Sequencers can perform all operations, including managing rewards and lock-ups, directly through these contracts without needing frontend access.

## **Key Contract Functionalities**

The following methods are provided to manage Sequencers efficiently. These include querying and updating your Sequencer's status, locking tokens, and handling rewards.

**Read Contract Information**

1. **`seqOwners`**
   * Retrieves all operational details of a Sequencer using the owner address.
   * **Parameter**:
     * `seqId (uint256)`: Sequencer ID.
   * **Response**: Detailed Sequencer operational state.
2. **`seqSigners`**
   * Retrieves Sequencer information using the signer address.
   * **Parameter**:
     * `seqId (uint256)`: Sequencer ID.
   * **Response**: Detailed Sequencer operational state.
3. **`sequencers`**
   * Accesses all relevant details of a Sequencer using its ID.
   * **Parameter**:
     * `seqId (uint256)`: Sequencer ID.
   *   **Response**:

       ```python
       pythonCopy codeamount (uint256) : Locked token amount
       reward (uint256) : Accrued rewards
       activationBatch (uint256) : Activation batch number
       updatedBatch (uint256) : Last updated batch number
       deactivationBatch (uint256) : Deactivation batch number
       deactivationTime (uint256) : Time of deactivation
       unlockClaimTime (uint256) : Time for claiming unlocked tokens
       nonce (uint256) : Nonce value
       owner (address) : Owner's address
       signer (address) : Signer's address
       pubkey (bytes) : Signer's public key
       rewardRecipient (address) : Address for reward distribution
       status (uint8) : Current Sequencer status
       ```

***

**Write Contract Information**

1. **`lockFor`**
   * Locks METIS tokens and assigns Sequencer ownership.
   * **Parameters**:
     * `_signer (address)`: Sequencer signer address.
     * `_amount (uint256)`: Amount of METIS to lock.
     * `_signerPubkey (bytes)`: Uncompressed public key of the signer.
2. **`lockWithRewardRecipient`**
   * Similar to `lockFor`, but allows specifying a reward recipient at the outset.
   * **Parameters**:
     * `_signer (address)`: Sequencer signer address.
     * `_rewardRecipient (address)`: Reward recipient address.
     * `_amount (uint256)`: Amount of METIS to lock.
     * `_signerPubkey (bytes)`: Uncompressed public key.
3. **`relock`**
   * Adds additional tokens to an existing lock or locks accrued rewards.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_amount (uint256)`: Amount to relock.
     * `_lockReward (bool)`: Whether to lock rewards.
4. **`setSequencerRewardRecipient`**
   * Updates or assigns a reward recipient for a Sequencer.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_recipient (address)`: New reward recipient address.
5. **`withdrawRewards`**
   * Withdraws accrued rewards to the specified address.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit for the operation.
6. **`unlock`**
   * Initiates the unlocking process for METIS tokens.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit for the bridge operation.
7. **`unlockClaim`**
   * Claims unlocked tokens after the 21-day waiting period.
   * **Parameters**:
     * `_seqId (uint256)`: Sequencer ID.
     * `_l2Gas (uint32)`: Gas limit.
8. **`withdraw`**
   * Partially withdraws locked tokens, ensuring the remaining balance meets the minimum lock requirement.
   * **Parameters**:
     * `_amount (uint256)`: Amount to withdraw.
     * `_seqId (uint256)`: Sequencer ID.
