<!-- README.md -->
# 🧾 MultiWill – Digital Inheritance on Flare (Coston2)

## 1. Project Title

**MultiWill – On-Chain Digital Inheritance Manager**

A smart contract–driven system that lets users create and manage multiple on-chain wills, assigning FLR (or compatible native tokens) to chosen recipients in a transparent and trust-minimized way.

---

## 2. Contract Address

The MultiWill contract is deployed on the **Flare Coston2 testnet**:

- **Contract Address:** `0xF302134fbC6525bD0be4cA2aA040f3A5F9ff8492`  
- **Block Explorer:** https://coston2-explorer.flare.network/address/0xF302134fbC6525bD0be4cA2aA040f3A5F9ff8492

You can view the contract, its transactions, and interact with it directly through the explorer.
<img width="1846" height="914" alt="image" src="https://github.com/user-attachments/assets/8dab423b-7017-4d44-8ea1-b99119127647" />


---

## 3. Description

MultiWill is a **decentralized digital inheritance system** built as a smart contract. It allows users to lock funds into “wills” that specify:

- A **recipient address**
- A **specific amount** of native tokens (e.g., FLR)
- A **claim status** (claimed / not claimed)

Each wallet can maintain **multiple wills**, enabling granular distribution of assets to different recipients.

Because MultiWill is deployed on-chain, it:

- Operates without centralized services, lawyers, or custodians.
- Relies on smart contract logic to enforce who can claim what.
- Stores all state on the blockchain for transparency and auditability.

The frontend integration (via `wagmi` + `viem`) provides a simple UI where users can:

- Connect their wallet.
- Create new wills by specifying a recipient and sending FLR.
- Trigger claims as a recipient.
- View contract balance and their personal will count.

---

## 4. Features

### 🔐 Trust-Minimized Digital Wills
- Users create wills directly on-chain.
- No need for traditional intermediaries (lawyers, custodians, centralized services).
- Contract logic strictly enforces ownership and recipient permissions.

### 🧾 Multiple Wills per Owner
- Each address can create **multiple separate wills**.
- Helpful for distributing funds among:
  - Family members
  - Friends
  - Organizations or charities

### 💰 Native Token Support
- Wills are funded in the network’s **native currency** (e.g., FLR on Flare Coston2).
- Amounts are stored per will and released only to the intended recipient.

### ✅ Recipient-Only Claiming
- Only the address designated as `recipient` in a will can successfully call `claimWill`.
- Once a will is claimed, it is marked as `claimed` to prevent double-claims.

### 📊 On-Chain Transparency
- Anyone can:
  - View the overall contract balance.
  - Query the number of wills created by an address.
  - Fetch details of individual wills (recipient, amount, claimed status).
- Ensures full visibility over the system’s state.

### 🧱 Simple, Composable API
Core functions exposed by the contract include:

- `createWill(address _recipient)` – create and fund a new will (payable).
- `claimWill(address _owner, uint256 _index)` – claim a specific will as the authorized recipient.
- `getMyWillsCount()` – count of wills created by the caller.
- `getWill(address _owner, uint256 _index)` – read details of a specific will.
- `getContractBalance()` – total balance locked in the contract.

These methods are easy to integrate into any dApp or backend using `viem` or `ethers`.

### 🧩 Frontend Integration (Sample UI)
The sample React/Next.js UI (`components/sample.tsx`) demonstrates:

- Wallet connection using `wagmi`.
- Reading contract state (balance, will count).
- Creating new wills with recipient validation.
- Triggering claims with error handling and transaction status feedback.

---

## 5. How It Solves the Problem

### The Problem

Traditional inheritance and asset transfer systems suffer from several issues:

1. **Centralization & Trust Requirements**
   - Require lawyers, custodians, or centralized platforms.
   - Introduce counterparty risk and potential single points of failure.

2. **Lack of Transparency**
   - Beneficiaries may not know the status, value, or details of what they are supposed to receive.
   - Processes are often slow, opaque, and jurisdiction-dependent.

3. **Poor Fit for Digital Assets**
   - Crypto and digital tokens are held in wallets, not bank accounts.
   - Traditional legal processes don’t integrate natively with blockchain assets.

4. **Complex Coordination**
   - Writing and executing a will across multiple beneficiaries can be complicated and costly.
   - Cross-border inheritance can be especially difficult.

---

### The MultiWill Solution

MultiWill addresses these pain points using **smart contract automation** and **on-chain data**.

#### 1. Direct, On-Chain Allocation
Owners can create wills directly from their wallet:

- They specify a **recipient address**.
- They send FLR as the **inheritance amount**.
- The will is stored in a public, auditable contract state.

This removes the need for intermediaries in the allocation step.

#### 2. Clear, Programmable Rules
The logic for inheritance is fully encoded in the contract:

- Only the **designated recipient** can claim funds.
- Once claimed, the will is marked as claimed and cannot be reused.
- Every interaction is recorded on the blockchain.

This delivers predictable behavior that doesn’t depend on human discretion.

#### 3. Full Transparency & Verifiability
Because everything is on-chain:

- Beneficiaries can verify:
  - That a will exists.
  - The amount assigned to them.
  - Whether it has been claimed.
- Third parties (auditors, apps, dashboards) can integrate and analyze state.

This transparency builds trust without exposing private keys or seed phrases.

#### 4. Easy Integration for dApps
The simple ABI and clean function design make MultiWill:

- Easy to use in **other DeFi / Web3 applications**.
- Suitable as a building block for:
  - Inheritance dashboards.
  - Legacy planning tools.
  - DAO or community-grant mechanisms (e.g., scheduled or conditional grants).

#### 5. Educational & Developer-Friendly
Deployed on **Flare Coston2 testnet**, this project also serves as:

- A learning resource for:
  - Writing multi-recipient, stateful smart contracts.
  - Integrating contracts with a modern frontend stack (`Next.js`, `wagmi`, `viem`).
- A template for developers who want to:
  - Build advanced inheritance logic (time locks, oracles, social recovery).
  - Extend the contract to more complex estate planning logic.

---

## Summary of Benefits

- **For Users:**  
  A straightforward way to allocate crypto assets to multiple recipients, enforced entirely by code.

- **For Developers:**  
  A clean, well-structured smart contract and React integration demonstrating multi-will management, ready to extend and adapt.

- **For the Ecosystem:**  
  A step toward practical, user-friendly digital inheritance on blockchain networks like Flare.

---
