# 🧠 zkConfide: Private, Personalized Betting Protocol

**zkConfide** is a next-gen prediction market protocol designed for privacy-preserving, personalized, and MEV-resistant betting experiences. It enables users to place on-chain bets on real-world events using USDC, with outcomes resolved via **zkProofs** and market dynamics powered by **Uniswap v4 Hooks**. Each user receives tailored betting suggestions based on risk appetite, powered by AI.

Built to defend against frontrunning and execution manipulation, zkConfide ensures all bets are executed transparently on-chain, while intent, user strategy, and outcome resolution remain private and policy-bound — safeguarding against MEV attacks, slippage abuse, and data leakage.

## 🧩 Uniswap V4 Hook Advance AMM – Base Sepolia

We successfully deployed the **PredictionMarketHook** contract on **Base Sepolia** using a CREATE2 deployer, enabling deterministic and permissionless hook address generation.

### 🔗 Deployment Transaction
**v4 Prediction Hook Contract on Base Sepolia:**  
[0x1Bcb64DB8e9EFd85f4323d841e4fF4826f6aCAC0](https://sepolia.basescan.org/address/0x1Bcb64DB8e9EFd85f4323d841e4fF4826f6aCAC0)

---

### ⚙️ Deployment Details

- **Deployer Address:**  
  [0x2cac89ABf06DbE5d3a059517053B7144074e1CE5](https://sepolia.basescan.org/address/0x2cac89ABf06DbE5d3a059517053B7144074e1CE5)

- **PoolManager Address:**  
  [0x05E73354cFDd6745C338b50BcFDfA3Aa6fA03408](https://sepolia.basescan.org/address/0x05E73354cFDd6745C338b50BcFDfA3Aa6fA03408)

- **CREATE2 Deployer Address:**  
  [0x4e59b44847b379578588920cA78FbF26c0B4956C](https://sepolia.basescan.org/address/0x4e59b44847b379578588920cA78FbF26c0B4956C)

- **Salt Used:**  
  `0x000000000000000000000000000000000000000000000000000000000000148e`

---

### 🪙 Token Contracts

- **USDC Token:**  
  [0xfF404DbD652F8f292374332Fc1Ed77AD3c726311](https://sepolia.basescan.org/address/0xfF404DbD652F8f292374332Fc1Ed77AD3c726311)

- **YES Token:**  
  [0xb38aF032736d034a89e9aF849Fa15eDFAf7e8F4A](https://sepolia.basescan.org/address/0xb38aF032736d034a89e9aF849Fa15eDFAf7e8F4A)

- **NO Token:**  
  [0xF465C26a7097B81F51Ae8385265b2F4C6D9511a2](https://sepolia.basescan.org/address/0xF465C26a7097B81F51Ae8385265b2F4C6D9511a2)

---


![image](https://github.com/user-attachments/assets/2c02794c-fddf-4374-a593-e9d29f762b02)


---

## 🌟 Key Features

### ✅ Social Login with Privy & nilQL
- Seamless onboarding using social login.
- A **server wallet** is instantiated via Privy for each user, allowing secure interaction with smart contracts using custom policies while abstracting private key management.

### 🎯 AI-Powered Risk Personalization with Nillion TEE (Secret LLM)
- Users select events and receive personalized odds and betting suggestions.
- AI models analyze user risk profiles and event data to recommend optimal YES/NO outcomes.

### 🧩 On-Chain Bets via Uniswap v4 Hooks
- Bets are placed on-chain using **USDC**, swapped into YES/NO outcome tokens via a **custom Uniswap v4 Hook** (`PredictionMarketHook`).
- Swaps are MEV-resistant and governed by internal hook logic to prevent front-running or manipulation.

### 💧 Liquidity Participation
- Users can add/remove liquidity in the YES/USDC and NO/USDC pools.
- LPs earn fees and indirectly help shape odds based on market depth.

### 🔐 Event Resolution via zkProofs
- Market outcomes are verified using **zkProofs** via `IProver`-based resolvers.
- zkOracles fetch results from off-chain trusted data sources and submit proofs on-chain.
- No single party can manipulate or delay market resolution.

### 💰 Trustless Winnings Settlement
- Token holders of the winning outcome redeem their tokens for USDC.
- zkProofs ensure that only valid claims can be executed on-chain.

### 🔄 Smart Fund Management
- After settlement, users can:
  - Reuse funds for new bets.
  - Withdraw privately from the server wallet to an external wallet.
  - Stay anonymous throughout via batched, private withdrawals.

---

## 🔁 Feature Flow

```text
1. User accesses zkConfide and logs in via social login.
2. A server wallet is instantiated to manage the user’s on-chain interactions.
3. The user selects an event to bet on.
4. AI model generates personalized odds based on risk and event data.
5. The user confirms a bet and swaps USDC for YES/NO tokens via Uniswap v4 Hook.
6. Bet is recorded on-chain, liquidity is updated dynamically.
7. Other users match the bet via the same AMM pool.
8. After the event, a zkProof is generated and submitted to verify the outcome.
9. Users holding the winning token redeem for USDC.
10. Funds are credited to their server wallet.
11. Users can withdraw to their private wallet or place new bets.
```
