---
description: >-
  This guide provides an overview of the various Metis networks along with their
  public RPC endpoints, making it easy for you to connect and start building
---

# Networks & RPC Endpoints

{% hint style="info" %}
NOTICE: **Metis is a native token but also an ERC20 compatible token on Layer 2.** It is a built-in feature, so there is no need to create a wrapped Metis token, and the source code is [here](https://github.com/MetisProtocol/mvm/blob/develop/packages/contracts/contracts/MVM/MVM_Coinbase.sol). Sushiswap team deployed a wMetis, it's the same with WETH9, the contract address is [0x75cb093E4D61d2A2e65D8e0BBb01DE8d89b53481](https://andromeda-explorer.metis.io/address/0x75cb093E4D61d2A2e65D8e0BBb01DE8d89b53481/contracts)

In case when you need higher limits of the public RPC endpoint, there are two options: 1. Setting up a private RPC endpoint using a provider such as [Nodies](https://www.nodies.app/) or [BlastAPI](https://blastapi.io/) 2. Setting up a [replica node](https://github.com/ericlee42/metis-replica-node)
{% endhint %}

<table data-header-hidden data-full-width="false"><thead><tr><th width="220">Network</th><th>Andromeda (Mainnet)</th><th>Sepolia (Testnet)</th></tr></thead><tbody><tr><td>Chain ID</td><td>1088 (Andromeda)</td><td>59902</td></tr><tr><td>Currency Symbol</td><td>Metis</td><td>tMetis</td></tr><tr><td>Explorer</td><td><a href="https://andromeda-explorer.metis.io/">https://andromeda-explorer.metis.io/</a></td><td><a href="https://sepolia-explorer.metisdevops.link/">https://sepolia-explorer.metisdevops.link/</a></td></tr><tr><td>HTTP RPC Endpoint</td><td><a href="https://andromeda.metis.io/?owner=1088">https://andromeda.metis.io/?owner=1088</a></td><td><a href="https://sepolia.metisdevops.link/">https://sepolia.metisdevops.link/</a></td></tr><tr><td>HTTP RPC by Community</td><td>Check <a href="https://docs.metis.io/dev/tools/rpc-endpoints">RPC endpoints</a></td><td></td></tr><tr><td>WebSocket RPC ENDPOINT</td><td>Check <a href="https://docs.metis.io/dev/tools/rpc-endpoints">RPC endpoints</a></td><td>wss://sepolia-ws.rpc.metisdevops.link</td></tr><tr><td>Contract Address</td><td>Refer to the Contract Addresses page</td><td>Refer to the Contract Addresses page</td></tr></tbody></table>
