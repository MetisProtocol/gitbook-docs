# Hardhat Set up

### **Hardhat Setup for Metis**

**Hardhat** is a popular Ethereum development environment that enables you to compile, deploy, test, and debug your smart contracts easily.

1. **Install Hardhat**: First, make sure you have Node.js installed. Then, in your project directory, run:

```markup
npm install --save-dev hardhat
```

2. **Create a Hardhat Project**: Initialize a new Hardhat project:

```bash
npx hardhat
```

Choose "Create a basic sample project" and follow the prompts.

3. **Configure Hardhat for Metis**: Edit the `hardhat.config.js` file to connect to the Metis network (either Andromeda Mainnet or Sepolia Testnet):

```
require("@nomiclabs/hardhat-waffle");

module.exports = {
  solidity: "0.8.4",
  networks: {
    metis: {
      url: "https://andromeda.metis.io/?owner=1088",  // Andromeda Mainnet
      accounts: [`0x${PRIVATE_KEY}`],  // Replace with your private key
    },
    sepolia: {
      url: "https://sepolia.metisdevops.link",  // Sepolia Testnet
      accounts: [`0x${PRIVATE_KEY}`],  // Replace with your private key
    },
  },
};

```

4. **Compile and Deploy**: Compile your contract:

```
npx hardhat compile
```

Deploy it with a simple script:

```
npx hardhat run scripts/deploy.js --network metis
```
