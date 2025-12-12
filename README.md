# NFT_Smart_contract
This project implements a simplified ERC-721–compatible NFT collection using Solidity and the Hardhat development environment.
It includes access control, metadata handling, test automation, and a Docker setup to compile and test the contracts in a fully isolated environment.

---
## Project Structure
```
nft-project/
│
├── contracts/
│   └── NftCollection.sol
│
├── test/
│   └── NftCollection.test.js
│
├── scripts/
│   └── deploy.js   (optional for deployment)
│
├── Dockerfile
├── hardhat.config.js
├── package.json
└── README.md
```
---
## Smart Contract Features
#### ERC-721–compatible skeleton
- Tracks ownership
- Balances
- Approvals
- Safe minting
- Token transfers

#### Access Control
- _admin state variable
- onlyAdmin modifier
- Pausing / unpausing minting

#### Metadata Support
- baseURI
- Dynamic tokenURI(tokenId) builder
- uintToString() helper

#### Supply Tracking
- maxSupply limit
- totalSupply counter

---
##  Running Tests (Hardhat)
To run tests locally:
```
npx hardhat test
```
Each test deploys a fresh contract instance and validates:
-  Initial configuration
- Admin-only minting
- Pause/unpause minting
- Transfers and approvals
- Token URI correctness
- Max supply enforcement

---
## Docker Usage
This project includes a Dockerfile that:
- Uses Node 20 Alpine
- Installs all dependencies
- Compiles the contract
- Runs the Hardhat test suite automatically
#### Build the Docker Image
```
docker build -t nft-contract .

```
#### Run the Tests Inside Docker
```
docker run nft-contract

```
Docker will:
- Install dependencies
- Compile the Solidity contracts
- Run the test suite as the default command

---
##   Tools and Versions
  Tool           Version
- Node.js	   --> 20.x
- Hardhat	   --> 2.x
- Solidity   --> ^0.8.0
- Docker	   --> Latest
- Base Image --> node:20-alpine

  ---
## Assumptions
- This project does not implement the full ERC-721 standard but provides a compatible interface for academic requirements.
- Metadata strategy uses baseURI + tokenId + ".json".
- Only the admin (deployer) can mint tokens.
- Minting can be paused and resumed.
