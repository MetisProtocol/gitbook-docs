# Mainnet Sequencer Operation Guide

The Decentralized Sequencer Pool is a critical step towards complete decentralization of Metis’ Layer 2 network, eliminating single points of failure associated with centralized sequencers. By combining existing decentralized P2P validators and block producers, it enhances stability, scalability, and fault tolerance.

{% hint style="warning" %}
Prerequisites to running a sequencer: Need to be approved by governance. See [How to become a sequencer](../how-to-become-a-sequencer/how-to-become-a-sequencer-mainnet.md) for more details.
{% endhint %}

## **Step 1: Set Up and Run Your Node**

Follow the provided technical documentation to deploy and initialize your Sequencer node:

**Initialization**:

1. Install and configure [Docker Compose](https://github.com/ericlee42/metis-sequencer-setup-docker-compose) or [Kubernetes](https://github.com/MetisProtocol/metis-charts/blob/main/README.md) on your server.
2. Run the Sequencer node setup script:
   * Generate the Sequencer address, private key, and public key during initialization.
3. Back up your private key securely. Loss of the key may result in irrecoverable consequences.

**Configuration**:

* Deploy your node as instructed in the README file using Docker Compose or Kubernetes.
* Ensure your private key address is backed up, and generate a local private key file for secure storage.

***

## **Step 2: Submit Sequencer Information**

Submit your node's details via a GitHub pull request for inclusion in the Metis Decentralized Sequencer Dashboard:

Refer to [Metis-Sequencer-Resources](https://github.com/MetisProtocol/metis-sequencer-resources) to submit your sequencer information:

**Required Information**:

* **Name**: Name of your Sequencer.
* **Avatar**: A profile image/logo.
* **URL**: Your organization's website or profile link (e.g., X.com link).
* **Address**: The whitelist address for sequencer lock-up.
* **Seq\_addr**: The sequencer address provided by the server after you run the Sequencer
* **Pubkey**: The public key provided by the server after you run the Sequencer. Please remove the extra ‘04’ characters from the generated pubkey..
* **Description**: Brief introduction about you or your organization.

**Submission Steps**:

1. Fork the [Metis-Sequencer-Resources Repository](https://github.com/MetisProtocol/metis-sequencer-resources).
2. Create a new branch and add your Sequencer details.
3. Submit a pull request for approval.

***

## **Step 3: Synchronize Your Node**

### Step 5:Wait for Sequencer Synchronization

Run the node and wait for block synchronization to complete:

1. Check the logs of the bridge container. Wait until the “`Waiting for themis to be synced`” message disappears, indicating that themis is synchronized to the latest height.
2. `Query eth_getBlockByNumber` via the l2geth RPC to confirm the block height if it is synchronized to the latest.

Once both the Bridge and L2geth are fully synchronized, you can proceed with the lock operation.

{% hint style="info" %}
Note: Ensure synchronization is complete before proceeding. Continuing operations before synchronization is finished may result in lock events not being recognized.
{% endhint %}

***

## **Step 4: Lock METIS Tokens**

## **Network Requirement**

{% hint style="info" %}
#### **The Metis tokens to be locked must be on Ethereum L1 (chainid:1)**
{% endhint %}

You can complete the locking process through the [Sequencer Mining page](https://sequencer.metis.io/). Alternatively, you can interact directly with the contract to bypass the frontend operations. Please refer to the “[Contract](https://docs.google.com/document/d/1iqCMU-v2l4vaT0uPbAt3pz64Mco9b2LdHZ3xfF59j3I/edit#heading=h.o1nnf1lvk3dk)” section for more details.

**Locking Options**

You can lock METIS tokens using one of the following methods:

1. **Via Sequencer Mining Page**:
   * Access the user-friendly interface to complete the locking process directly through the [Sequencer Mining page](https://sequencer.metis.io/).
2. **Direct Contract Interaction**:
   * For advanced users, bypass the frontend and interact directly with the smart contract. Refer to the **"**[**Contract**](https://docs.google.com/document/d/1iqCMU-v2l4vaT0uPbAt3pz64Mco9b2LdHZ3xfF59j3I/edit#heading=h.o1nnf1lvk3dk)**"** section for detailed instructions and required method calls.

\\

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfcSiP78QHfnJAm6aPAB-vl_ho3fbqx2mlFW-v1TYz31nwvTGwqpH6pAXLHiTRFvVn1Cjs1-41Byuh-Mgkk1HtcBnSFK0I1JA6_JVvc3QbSlw9XyxHnoC1uvMI3i_Th1asjzRKJdUWohI_2JMqddngP0PVt?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

**Wallet Whitelisting**

Once your wallet address is added to the whitelist, you'll notice a **"Become a Sequencer"** button after connecting your MetaMask wallet. To initiate the process:

1. **Connect Your Wallet**: Ensure your MetaMask is connected to the Ethereum network.
2. **Start the Process**: Click the **"Become a Sequencer"** button to begin.

**Pre-Requisites**

Before proceeding:

* **Minimum METIS Tokens**: Ensure your wallet holds at least **20,000 METIS** on the Ethereum mainnet.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdmnokEuLGbUzXCGLVsCEZj3cpAvy1GxabXBYl0RN-k7MlAPUoN1-CeC1NipPMOBztmq4QLQjtAmV3VQMrOJXNeeJZd2rIbl1EY9cSr9x9IVGtfzAq36avxXTK0i3R-YU_YqMI4rBpZWUHNn3rykSc_Eyzv?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

**Node Setup**

Set up your Sequencer node using Kubernetes for deployment. While Kubernetes is the recommended method for deployment, additional deployment options will be introduced in the future.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXehgOxuKDwRCyXIhGzAlCsrHxuI_RSy9C8yxxj60fwXUvn_h2w10a5tEzxunvfK6X3ZdqsWHAorD8u7yFETuLVxgOCkWaAdEjR2WF-oeJRtUABbv9Afg0idI0LW5GCr8m0gxkJ7uKmJ0BF8Jgx-NYD_5vUo?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

**Token Lock-Up**

The lock-up process is a critical step for participating in the Sequencer Pool:

1. **Lock-Up Amount**:
   * Enter the amount of METIS tokens you want to lock, ensuring a **minimum of 20,000 METIS** and a **maximum of 100,000 METIS**.
2. **Confirm Transaction**:
   * Click **"CONFIRM"** to execute the lock-up transaction and confirm it in your wallet.

***

**Important Considerations**

* **Lock-Up Cap**: The maximum lock-up amount is 100,000 METIS. Transactions exceeding this cap will still execute; however, rewards will be calculated based on the capped amount of 100,000 METIS.
* **Partial Withdrawals**: The functionality to partially withdraw locked tokens is not available yet. If you accidentally lock more than intended, you will need to exit and rejoin the Sequencer Pool. Note that there is a **21-day exit period**, during which rewards will not accrue.
* **Plan Carefully**: Only lock the amount of METIS you are comfortable with, keeping in mind the operational limits and restrictions.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe-ukWP3V54wOO9oHrQyEmqTzE6dD589CBgulPGRiSl6LZ0-GHP5YdiyHWf3FyK1CUrtKPudgDSJgs3gDxqPwbDK2Jx8-ZXyEiSZA4r_1cYIANzTYkh9WOh8SHXQVL6yd2AxQT4ajwCHKIf7-rgtp4yIP_i?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

**Completion**

Once the lock-up process is complete and you see the **"Complete"** confirmation page, congratulations—your Sequencer setup is now successful, and you are ready to operate as part of the Metis Decentralized Sequencer Pool.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXebnPM_dtuIuEnBoHXvNARjHUTI2sPV3ke76CeteONI96qb8qXhbb-17dbe4kJF_BJtnmX_6EpHr_HfsdrjGH8FontRahPQZK-eP-o4C8cXO39VgrXBeTmqD9TmlOFOQTBCTfuTpglVmOT77sJgDbGPrvw?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

**Important**:

* Rewards are capped at 100,000 METIS lock-up.
* Withdrawals before the 21-day exit period are not allowed.

***

## **Step 5:** Activate Your Sequencer and Monitor via the Dashboard

1.  Once your Sequencer node is successfully running, proceed to the **Sequencer Dashboard** to monitor and manage your node.

    **What You Can Do on the Dashboard:**

    * **View Operational Metrics**: Access real-time data about your Sequencer's performance, such as block production status and synchronization progress.
    * **Check Rewards**: Monitor your earned mining rewards and track reward distribution details.
    * **Node Health Status**: Ensure your node is operational and meeting network requirements.

    This centralized dashboard provides you with a streamlined view of all essential metrics, making it easier to manage and optimize your Sequencer operations.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeVErpi12f1AtsR0bOOO0qbnWmzkUxaVDhTKewB9ybQ4X16KHsuxEL7H5JFL4-kO83WDTAfKPan-hCFeHcJtHfjlTWzsCLHLvtfPIE1CT2y6g1QEgoAzKkle5U6AH7GOlPJbt7eANodJELmQW-QfEbcL6IE?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

## **Step 6:** Daily Operations and Support

To ensure your Sequencer operates efficiently and generates consistent earnings, follow these guidelines:

## **Daily Maintenance**

1. **Server and Network Health**:
   * Maintain a stable server environment and network connection.
   * Regularly monitor your node’s performance metrics to ensure proper block packaging and production.
2. **Log Monitoring**:
   * Review system logs frequently to detect and resolve any issues promptly.
3. **Software Updates**:
   * Keep your Sequencer node software updated to the latest version to avoid compatibility issues and ensure optimal performance.

## **Community Support**

If you encounter any issues or need assistance:

* **Join the Community**: Connect with other Sequencer operators on the Metis Sequencer group via:
  * **Discord**
  * **Telegram**
* **Get Quick Help**: These groups provide real-time communication and a platform to share solutions and receive technical support from the Metis team and the community.

Efficient daily operations and active engagement with the community will help you maintain your node's uptime and maximize your earnings.

***

## **Step 7: Claim Mining Rewards**

Once your Sequencer starts earning rewards, you can claim them through the **Sequencer Dashboard**:

{% hint style="warning" %}
Please double-check your wallet address before submitting. If you are using a contract address, make sure it is the correct contract address on Metis Andromeda. Entering an incorrect address could result in the loss of rewards.
{% endhint %}

**Steps to Claim Rewards:**

1.  **View Unclaimed Rewards**:

    * Navigate to the Dashboard to check your current unclaimed rewards.
    *

    ```
    <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfjsEdXNoY82vJQK2xg7hiP8LhFo7GEZKKCxypUSHsTPlLQuEg77CHSg2sDHrl94rj4dk624BnBpY0IPp_uiRi4RHsjWLP263fz0z4qnmOJpIFGGKFLAM4uxwg7yd2vAl5LGA2qe2qqJprc7LByH4g-8ulF?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>
    ```
2.  **Initiate Claim Transaction**:

    * Click the **"Claim"** button to begin the reward distribution process.
    *

    ```
    <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdKjEYVCyzhlirJRgdXsnE4g4OQ-KFbWpNXMFbCvXdUchNC_z9XT1ECDX3lgFAa8hsZ3OHKOHYwcKH8Pvqpzkc3CVi4Csuv8nH176o1qx36l6_HlSwNa7-vWZjJXVprV0qCNNIgPRacUT1SPTMR-_WIZzGT?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>
    ```
3. **Confirm or Modify Wallet Address**:
   * Verify your wallet address in the popup window.
   * If needed, modify the address before submitting the transaction.
4. **Rewards Distribution**:
   * The rewards will be transferred to your specified address on the Metis Andromeda network.

**Important Notes:**

* Double-check your wallet address to avoid errors.
* For contract addresses, ensure the address is correct and active on the **Metis Andromeda** network to prevent the loss of rewards.

***

#### **Additional Practices**

**Increasing Your Lock-Up Amount**

1. **Dashboard Update**:
   * On the Sequencer Dashboard, view the current amount of locked METIS.
2. **Increase Lock-Up**:
   * Enter the additional METIS amount in the **"Increase"** field and confirm the transaction.
3. **Maximum Cap**:
   * The lock-up cap remains at **100,000 METIS**. Attempts to lock more will not yield additional rewards.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfOHDwV9uf8j_WW6HYxLW8BqbcYQ-zvP2uXjinjdxPh0Uo7EwyQzo78rSH4WwPY5guD8fffKIp3ASkuKGuGXSvKf2cMTHCWxid9QDYGzfh9DJ0SacpY4gjIkmmcJRJCNl8XVYaWx2xxzuzbSDL9mul5kvLC?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

**Partial Withdrawals**

1. **Eligibility**:
   * You can withdraw any amount exceeding the **20,000 METIS minimum** lock-up.
   * The withdrawable amount is calculated as:\
     \&#xNAN;_Total locked tokens – 20,000 METIS._
2. **Initiate Withdrawal**:
   * On the Dashboard, click **"Partial Withdraw."**
   * Enter the desired amount, confirm the transaction in the popup, and validate it in MetaMask.
3. **Token Transfer**:
   * The withdrawn METIS will be sent to your **Owner address**.

1

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXewYE8dxh5o8iWQe7IuLlGk5vjWThbPmROW7arnugH2VRUEYDEL7H9kHH31YlswLuRT00qgbBJylk_m3BZV_cA2ekh-xhImaVbIuVLqKFuzBFyGHNuluw1KG693WiDLREVWOCY7TqBj-Tysyn3hmHmai6bB?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

**Exiting the Sequencer Pool**

1. **Initiate Unlock**:
   * Click the **"Unlock"** button on the Dashboard and confirm the exit transaction in MetaMask.
2. **21-Day Exit Period**:
   * Your Sequencer will enter a **21-day waiting period** during which:
     * Rewards will not be earned.
     * Block production will stop.
3. **Final Withdrawal**:
   * After 21 days, return to the Dashboard to withdraw your locked METIS.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdsdSyTwJA11LQ4qHYY5cX3Icu0721WChUC3_PCFRBj9DA_rHKvR1S7zMeVVZu50ZIhoELLRi9SJE07s_towvZK31s32SEKxRHJhveYx58YhF38VyLQIzAAHxam4zwW0hW8tYAaUJX9y0aIITU9SgYfdQ4?key=ZcS2C03A_szr_7RFlCMz8A" alt=""><figcaption></figcaption></figure>

***

#### **Sequencer Mining Rewards**

**Mining Reward Rate (MRR):**

* The **Estimated MRR** is **20%**, designed to incentivize Sequencer participation.
* Rewards are calculated per block and updated every two weeks to maintain the target MRR.

By following these guidelines, Sequencers can efficiently claim rewards, increase or withdraw their lock-up amounts, and avoid penalties while contributing to the security and stability of the Metis network.
