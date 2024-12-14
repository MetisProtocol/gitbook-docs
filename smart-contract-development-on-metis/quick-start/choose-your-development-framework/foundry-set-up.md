# Foundry Set up

### **Foundry Setup for Metis**

**Foundry** is a fast and powerful framework for Ethereum development, written in Rust. It’s great for developers who prefer more control and speed in their development workflows.

1. **Install Foundry**: Install Foundry by running the following command in your terminal:

```
curl -L https://foundry.paradigm.xyz | bash
```

Then, initialize Foundry:

```
foundryup
```

2. **Create a Foundry Project**: Start a new project:

```
forge init my-foundry-project
```

3. **Configure Foundry for Metis**: You will need to edit the `foundry.toml` file to include Metis network details:

```
[profile.default]
rpc_endpoints = { 
    metis = "https://andromeda.metis.io/?owner=1088",  # Andromeda Mainnet
    sepolia = "https://sepolia.metisdevops.link"  # Sepolia Testnet
}
```

4. **Compile and Deploy**: Compile your contracts:

```
forge build
```

Deploy using Foundry:

```
forge create --rpc-url https://andromeda.metis.io/?owner=1088 --private-key PRIVATE_KEY src/MyContract.sol:MyContract
```
