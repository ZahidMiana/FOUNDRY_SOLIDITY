# SimpleStorage Foundry Project

A simple smart contract project built with Foundry that demonstrates basic storage operations on the Ethereum blockchain.

## Project Overview

This project contains a `SimpleStorage` smart contract that allows users to:
- Store and retrieve a favorite number
- Add people with their names and favorite numbers
- Query favorite numbers by name using a mapping

## Contract Features

### SimpleStorage.sol
- **Store Function**: Save a favorite number to the blockchain
- **Retrieve Function**: Get the stored favorite number
- **Add Person**: Store a person's name and their favorite number
- **Name Mapping**: Query favorite numbers by person's name

## Project Structure

```
Foundry/
├── src/
│   └── SimpleStorage.sol          # Main smart contract
├── script/
│   └── DeploySimpleStorage.s.sol  # Deployment script
├── test/
│   └── (test files)
├── .env                           # Environment variables
├── foundry.toml                   # Foundry configuration
└── README.md                      # This file
```

## Prerequisites

- [Foundry](https://getfoundry.sh/) installed
- [Git](https://git-scm.com/) installed
- Basic knowledge of Solidity and Ethereum

## Installation & Setup

1. **Install Foundry** (if not already installed):
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   foundryup
   ```

2. **Clone or navigate to the project**:
   ```bash
   cd /home/zahid/Downloads/Foundry
   ```

3. **Install dependencies**:
   ```bash
   forge install
   ```

4. **Create environment file** (`.env`):
   ```bash
   PRIVATE_KEY=your_private_key_here
   RPC_URL=http://127.0.0.1:8545
   SEPOLIA_RPC_URL=https://eth-sepolia.g.alchemy.com/v2/your_api_key
   ```

## Usage

### 1. Compile Contracts
```bash
forge build
```

### 2. Run Tests
```bash
forge test
```

### 3. Start Local Network (Anvil)
```bash
anvil
```
This starts a local Ethereum node at `http://127.0.0.1:8545`

### 4. Deploy Contract

**Load environment variables:**
```bash
source .env
```

**Deploy to local network:**
```bash
forge script script/DeploySimpleStorage.s.sol:DeploySimpleStorage --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
```

**Deploy to Sepolia testnet:**
```bash
forge script script/DeploySimpleStorage.s.sol:DeploySimpleStorage --rpc-url $SEPOLIA_RPC_URL --broadcast --private-key $PRIVATE_KEY
```

### 5. Interact with Contract

**Store a favorite number:**
```bash
cast send <CONTRACT_ADDRESS> "store(uint256)" 42 --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

**Retrieve the stored number:**
```bash
cast call <CONTRACT_ADDRESS> "retrieve()" --rpc-url $RPC_URL
```

**Add a person:**
```bash
cast send <CONTRACT_ADDRESS> "addPerson(string,uint256)" "Alice" 25 --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

**Get person's favorite number:**
```bash
cast call <CONTRACT_ADDRESS> "nameToFavouriteNumber(string)" "Alice" --rpc-url $RPC_URL
```

## About Foundry

Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust. It consists of:

### Core Tools

- **Forge**: Ethereum testing framework (like Hardhat, Truffle, DappTools)
- **Cast**: Swiss army knife for interacting with EVM smart contracts
- **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network
- **Chisel**: Fast, utilitarian, and verbose Solidity REPL

### Key Features

- **Fast**: Written in Rust for maximum performance
- **Portable**: No dependencies on Node.js or Python
- **Modular**: Each tool can be used independently
- **Testing**: Comprehensive testing framework with fuzzing
- **Gas Reporting**: Built-in gas usage analysis
- **Debugging**: Advanced debugging capabilities

### Why Foundry?

1. **Speed**: Compile and test contracts faster than other frameworks
2. **Solidity-first**: Write tests in Solidity, not JavaScript
3. **Advanced Testing**: Built-in fuzzing and property testing
4. **No Dependencies**: Single binary installation
5. **EVM Compatibility**: Full compatibility with Ethereum Virtual Machine

## Common Commands

### Foundry Workflow
```bash
# Initialize new project
forge init my_project

# Install dependencies
forge install

# Compile contracts
forge build

# Run tests
forge test

# Deploy contracts
forge create SimpleStorage --rpc-url $RPC_URL --private-key $PRIVATE_KEY

# Run deployment script
forge script script/Deploy.s.sol --broadcast --rpc-url $RPC_URL

# Format code
forge fmt

# Generate gas report
forge test --gas-report
```

### Cast Utilities
```bash
# Get balance
cast balance <address> --rpc-url $RPC_URL

# Get block info
cast block latest --rpc-url $RPC_URL

# Convert units
cast to-wei 1 ether
cast from-wei 1000000000000000000

# Generate wallet
cast wallet new
```

## Testing

Run the test suite:
```bash
forge test -v  # Verbose output
forge test --gas-report  # Include gas usage
forge test --coverage  # Coverage report
```

## Configuration

Foundry configuration is in `foundry.toml`:
```toml
[profile.default]
src = 'src'
out = 'out'
libs = ['lib']
solc_version = "0.8.18"
```

## Security Considerations

⚠️ **Important Security Notes:**
- Never commit private keys to version control
- Use `.env` files for sensitive data
- Always test on testnets before mainnet deployment
- Verify contracts on Etherscan after deployment

## Troubleshooting

### Common Issues

1. **"Could not find target contract"**
   - Ensure contract name matches file name
   - Use format: `script/Deploy.s.sol:DeployContract`

2. **"Connection refused"**
   - Start Anvil: `anvil`
   - Check RPC URL in `.env`

3. **"Private key error"**
   - Ensure `.env` file is sourced: `source .env`
   - Check private key format (with or without 0x prefix)

## Resources

- [Foundry Documentation](https://book.getfoundry.sh/)
- [Foundry GitHub](https://github.com/foundry-rs/foundry)
- [Solidity Documentation](https://docs.soliditylang.org/)
- [Ethereum Development](https://ethereum.org/developers/)

## License

This project is licensed under the MIT License.

---
