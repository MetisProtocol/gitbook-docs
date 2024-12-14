# Truffle Set up

### T**ruffle Setup for Metis**

**Truffle** is another robust development environment, testing framework, and asset pipeline for Ethereum-based smart contracts.

1. **Install Truffle**: Ensure that you have Node.js installed, then globally install Truffle:

```
npm install -g truffle
```

2. **Create a Truffle Project**: Initialize a new Truffle project:

```
truffle init
```

3. **Configure Truffle for Metis**: Modify the `truffle-config.js` file to include Metis network configurations:

```
const HDWalletProvider = require('@truffle/hdwallet-provider');
const privateKey = process.env.PRIVATE_KEY;  // Use your private key

module.exports = {
  networks: {
    metis: {
      provider: () => new HDWalletProvider(privateKey, "https://andromeda.metis.io/?owner=1088"),
      network_id: 1088,  // Metis Andromeda Mainnet
    },
    sepolia: {
      provider: () => new HDWalletProvider(privateKey, "https://sepolia.metisdevops.link"),
      network_id: 59902,  // Sepolia Testnet
    },
  },
  compilers: {
    solc: {
      version: "0.8.4",  // Fetch exact version from solc-bin (default: truffle's version)
    },
  },
};

```

4. **Compile and Deploy**: Compile your contracts:

```
truffle compile
```

Deploy them:

```
truffle migrate --network metis
```
