# Foundry Fund Me

This project is part of the **Cyfrin Solidity Course**.

Course link:
[https://updraft.cyfrin.io/courses/foundry/foundry-fund-me/fund-me-project-setup](https://updraft.cyfrin.io/courses/foundry/foundry-fund-me/fund-me-project-setup)

---

## About

This project implements a minimal funding smart contract.

- Users send ETH to the contract
- ETH value is converted to USD using a Chainlink price feed
- Each contribution must meet a minimum USD threshold or the transaction reverts
- The contract tracks funders and contributed amounts
- Only the contract owner can withdraw collected funds

---

## Getting Started

### Requirements

- **Git**

  - Verify installation:

    ```bash
    git --version
    ```

- **Foundry**

  - Install from [https://getfoundry.sh/](https://getfoundry.sh/)
  - Verify installation:

    ```bash
    forge --version
    ```

---

### Quickstart

Clone the repository.

```bash
git clone https://github.com/Cyfrin/foundry-fund-me-cu
cd foundry-fund-me-cu
```

Build the project.

```bash
make
```

---

## Usage

### Deploy

Run the deploy script locally or on a configured network.

```bash
forge script script/DeployFundMe.s.sol
```

---

### Testing

This project focuses on two testing tiers:

- Unit tests
- Forked tests

Run all tests.

```bash
forge test
```

Run a specific test.

```bash
forge test --match-test testFunctionName
```

Run tests on a forked network.

```bash
forge test --fork-url $SEPOLIA_RPC_URL
```

---

### Test Coverage

Generate a coverage report.

```bash
forge coverage
```

---

## Deployment to a Testnet or Mainnet

### Environment Variables

Set the following environment variables. You may store them in a `.env` file.

- **PRIVATE_KEY**

  - Development key with no real funds

- **SEPOLIA_RPC_URL**

  - Sepolia RPC endpoint
  - Obtain one from [https://alchemy.com](https://alchemy.com)

- **ETHERSCAN_API_KEY** (optional)

  - Required for contract verification

---

### Get Testnet ETH

Use a faucet to obtain Sepolia ETH.

[https://faucets.chain.link/](https://faucets.chain.link/)

---

### Deploy

Deploy and verify on Sepolia.

```bash
forge script script/DeployFundMe.s.sol \
  --rpc-url $SEPOLIA_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast \
  --verify \
  --etherscan-api-key $ETHERSCAN_API_KEY
```

---

## Scripts

After deployment, you can interact with the contract.

### Fund

```bash
cast send <FUNDME_CONTRACT_ADDRESS> "fund()" \
  --value 0.1ether \
  --private-key <PRIVATE_KEY>
```

Or use a script.

```bash
forge script script/Interactions.s.sol:FundFundMe \
  --rpc-url sepolia \
  --private-key $PRIVATE_KEY \
  --broadcast
```

---

### Withdraw

Withdraw funds as the owner.

```bash
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()" \
  --private-key <PRIVATE_KEY>
```

---

## Gas Estimation

Generate a gas snapshot.

```bash
forge snapshot
```

This produces a `.gas-snapshot` file.

---

## Formatting

Format the codebase.

```bash
forge fmt
```

---

## Summary

- The Chainlink repository used is official
- It follows the official Chainlink release process
- It avoids pulling unreleased code directly

---
