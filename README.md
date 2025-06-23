
# 🌉 Solana ↔ Qubic Bridge Proposal

## 🔎 Overview

This project proposes the development of a secure and decentralized bridge that connects the **Qubic (non-EVM)** blockchain with **Solana**, enabling bi-directional token transfers between the two networks.

The bridge allows users to convert Qubic’s native token (**Qu**) to wrapped tokens (**wQUBIC**) on Solana and back. It includes smart contracts on both chains, a backend relayer, and a user-friendly frontend interface.

---

## ⚙️ How It Works

### 1. User Interface (Frontend)
- Built using **Next.js** and **Tailwind CSS**
- Connects to:
  - **Phantom Wallet** for Solana
  - **Metamask Snap** (experimental) for Qubic
- Lets users:
  - Choose swap direction (Qubic → Solana or Solana → Qubic)
  - Enter swap amount
  - Track transaction status

### 2. Smart Contract Operations
- **Qubic → Solana**:
  - Qubic smart contract locks Qu tokens
  - Relayer verifies and triggers minting of `wQUBIC` on Solana

- **Solana → Qubic**:
  - Solana program burns `wQUBIC`
  - Relayer verifies and triggers unlocking of Qu on Qubic

### 3. Relayer Backend (Python)
- Monitors both chains for lock/burn events
- Validates transactions and ensures replay protection
- Relays verified instructions to execute swaps
- Exposes APIs for frontend to display real-time status

---

## 🎯 Objectives

- Enable two-way token swaps between Qubic and Solana
- Deliver a secure, audit-ready bridge system
- Provide intuitive frontend for users to manage swaps
- Deploy smart contracts and relayer on testnet and mainnet

---

## 🔄 Swap Flow Summary

| Direction        | Origin Chain Action             | Relayer (Backend)            | Destination Chain Action              |
|------------------|----------------------------------|-------------------------------|----------------------------------------|
| **Qu → wQUBIC**  | Lock Qu tokens in Qubic smart contract | Validate lock event and construct relay message | Mint `wQUBIC` tokens to user on Solana |
| **wQUBIC → Qu**  | Burn `wQUBIC` tokens via Solana program | Validate burn and construct relay message | Unlock Qu tokens to user on Qubic      |

- Relayer ensures:
  - Event detection
  - Message formatting
  - Signature validation
  - Replay protection
- Destination chain validates relayed data before executing the mirrored action


## 📦 Scope of Work

### ✅ Included
- Qubic and Solana smart contract development
- Python-based backend relayer
- Next.js + Tailwind frontend interface
- Metamask Snap integration for Qubic
- Testnet and mainnet deployments
- Basic documentation

### ❌ Not Included
- Ongoing liquidity/fund management
- External third-party audit costs

---

## 💰 Budget Breakdown

| Component                           | Cost (USD)     |
|-------------------------------------|----------------|
| Smart Contract Development          | $6,250         |
| Backend Relayer (Python)            | $6,250         |
| Frontend (Next.js + Tailwind CSS)   | $5,000         |
| Final Deployment & Audit Prep       | $7,500         |
| **Total**                           | **$25,000**    |

> No PM or coordination fees included.

---

## 📆 Milestones

### 🧱 Milestone 1: Smart Contract Development (25%) — **$6,250**

This milestone delivers smart contracts for token swap logic.

**Deliverables:**
- Qubic contract to lock/unlock Qu
- Solana program to mint/burn `wQUBIC`
- Deploy to Qubic and Solana testnets
- Manual validation of token flows

---

### 🔁 Milestone 2: Backend Relayer Development (25%) — **$6,250**

A Python service that monitors both chains, validates actions, and relays messages.

**Deliverables:**
- Relayer that listens to on-chain events
- Validates and relays cross-chain transactions
- Implements nonce/replay protection
- REST API for frontend integration

---

### 🖥 Milestone 3: Frontend Development (20%) — **$5,000**

Build a responsive frontend for users to interact with the bridge.

**Deliverables:**
- UI built with Next.js and Tailwind
- Phantom and Metamask Snap integration
- Swap form and status tracking
- Integration with backend API

---

### 🚀 Milestone 4: Deployment, Integration & Audit (30%) — **$7,500**

Production deployment and integration testing of the complete system.

**Deliverables:**
- Deploy smart contracts and relayer to mainnet
- End-to-end test of both directions
- Documentation and audit-ready code
- Optional support for external audit

---

## 📝 Final Notes

- Qubic wallet support will rely on **Metamask Snap integration**
- The project will be developed with a modular, security-first mindset
- A third-party audit is **strongly recommended** prior to public launch
- Future enhancements (fee routing, MPC relayers, liquidity tools) can be proposed post-MVP

