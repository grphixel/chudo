# Base dApp Starter (Hardhat + Next.js) — Base mainnet

This repository is a starter dApp targeting Base (Coinbase Layer-2) mainnet (chainId: 8453). It includes a minimal Hardhat (TypeScript) smart contract project and a Next.js + TypeScript frontend that connects wallets via wagmi + RainbowKit and interacts with the deployed contract.

Quick start (mainnet)

1. Copy `.env.example` -> `.env` and fill values (do NOT commit this file):
   - BASE_MAINNET_RPC_URL
   - PRIVATE_KEY (deployer)
   - ETHERSCAN_API_KEY (optional)
   - NEXT_PUBLIC_BASE_RPC
   - NEXT_PUBLIC_CONTRACT_ADDRESS (set after deploy)

2. Deploy contracts (from `contracts/`):
   - cd contracts
   - npm install
   - npx hardhat compile
   - npx hardhat test
   - npx hardhat run --network baseMainnet scripts/deploy.ts

3. Update frontend env (frontend/.env.local) with NEXT_PUBLIC_CONTRACT_ADDRESS and NEXT_PUBLIC_BASE_RPC, then build/start frontend:
   - cd frontend
   - npm install
   - npm run dev

Notes
- Deploying to Base mainnet spends real funds. Ensure the deployer PRIVATE_KEY account is funded and you understand gas costs.
- Never commit private keys or RPC secrets. Use repository/CI secrets instead.

Files added
- contracts/: Hardhat + TypeScript (SimpleStorage contract, deploy script, test)
- frontend/: Next.js + TypeScript, wagmi + RainbowKit + ethers v6, simple UI to read/write the contract
- .github/workflows/ci.yml: basic CI to compile contracts, run tests, and build frontend
