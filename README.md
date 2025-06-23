proposal_md = """
# 🌉 Solana ↔ Qubic Bridge Proposal

## 🔎 Overview

This project aims to develop a robust, secure, and fully decentralized cross-chain bridge connecting the **Qubic blockchain (a non-EVM platform)** with the high-performance **Solana network**. This bridge will enable seamless, trust-minimized bi-directional token transfers, empowering users to convert native Qubic tokens (**Qu**) into wrapped tokens (**wQUBIC**) on Solana and redeem them back on Qubic.

By implementing this interoperability layer, the bridge unlocks enhanced liquidity, broader DeFi integration opportunities, and cross-chain asset mobility for users of both ecosystems. The solution will comprise well-audited smart contracts on both blockchains, a reliable backend relayer service for secure message relay and validation, and an intuitive frontend interface facilitating smooth user interactions.

---

## ⚙️ How It Works

### 1. User Interface (Frontend)
The frontend application, developed using **Next.js** and styled with **Tailwind CSS**, provides a responsive and intuitive user experience. It enables users to seamlessly connect their wallets—**Phantom** for Solana and **Metamask Snap** (currently experimental) for Qubic. Through this interface, users select the desired token swap direction, specify the amount, and initiate the transaction while tracking its real-time status.

### 2. Smart Contract Operations
On the blockchain layer, carefully designed smart contracts enforce token custody and minting logic:

- **Qubic → Solana**: When a user initiates a swap from Qubic to Solana, the Qubic smart contract securely locks the specified amount of Qu tokens. Upon successful lock confirmation, the backend relayer validates the event and triggers the minting of an equivalent amount of wrapped tokens (`wQUBIC`) on the Solana network.

- **Solana → Qubic**: Conversely, when transferring from Solana back to Qubic, the Solana program burns the user’s `wQUBIC` tokens. The backend confirms the burn event before instructing the Qubic smart contract to release the equivalent amount of Qu tokens to the user’s wallet.

### 3. Relayer Backend (Python)
The bridge’s backend, implemented in Python, operates as a secure, event-driven relayer service. It continuously monitors both blockchains for relevant events (token locks and burns), verifies transaction validity, protects against replay attacks, and orchestrates cross-chain communication by relaying validated instructions to the destination network. Additionally, it exposes RESTful APIs allowing the frontend to fetch transaction statuses and swap histories for a transparent user experience.

---

## 🔄 Swap Flow Summary

| Swap Direction   | Origin Chain Action                     | Backend Relayer Role                      | Destination Chain Action               |
|------------------|----------------------------------------|------------------------------------------|--------------------------------------|
| **Qu → wQUBIC**  | User locks Qu tokens in the Qubic smart contract | Detect and validate lock event, construct secure relay message | Mint equivalent `wQUBIC` tokens to user's Solana wallet |
| **wQUBIC → Qu**  | User burns `wQUBIC` tokens in the Solana program | Detect and validate burn event, construct secure relay message | Unlock equivalent Qu tokens to user's Qubic wallet |

**Key Relayer Responsibilities:**
- Real-time event monitoring on both chains  
- Robust validation and signature verification  
- Replay protection to prevent duplicate transactions  
- Reliable message formatting and forwarding  

The destination chain smart contracts verify all relayed data to ensure security and integrity before executing token minting or unlocking.

---

## 🎯 Objectives

The primary objective of this project is to establish a secure, efficient, and user-friendly bridge enabling seamless token interoperability between the Qubic and Solana blockchains. This involves:

- Designing and deploying robust smart contracts that guarantee the secure locking, unlocking, minting, and burning of tokens across both chains.
- Developing a reliable backend relayer system responsible for secure cross-chain communication, event validation, and prevention of replay or double-spend attacks.
- Creating an intuitive, responsive frontend interface that simplifies wallet connections and swap operations for end users.
- Ensuring the entire system is scalable, maintainable, and prepared for production deployment with comprehensive documentation and audit readiness.

---

## 📦 Scope of Work

### ✅ Included Deliverables
- **Smart Contract Development:**  
  Design, implement, and deploy smart contracts on Qubic and Solana to facilitate secure token locking, unlocking, minting, and burning.

- **Backend Relayer Service:**  
  Build a Python-based backend responsible for monitoring blockchain events, validating transactions, securely relaying cross-chain messages, and exposing APIs for frontend integration.

- **Frontend Development:**  
  Develop a responsive and user-friendly frontend using **Next.js** and **Tailwind CSS**. Integrate wallet support via **Phantom** (Solana) and **Metamask Snap** (Qubic).

- **Testnet & Mainnet Deployments:**  
  Deploy all components on respective testnets for validation, followed by mainnet deployment.

- **Documentation:**  
  Provide comprehensive developer and user documentation detailing architecture, APIs, and usage guidelines.

### ❌ Exclusions
- **Liquidity and Fund Management:**  
  Ongoing management of liquidity pools, token allowances, or fee distribution is not covered.


---

## 💰 Budget Breakdown

| Component                          | Description                                         | Cost (USD) |
|----------------------------------|-----------------------------------------------------|------------|
| **Smart Contract Development**    | Implementation and deployment of Qubic and Solana smart contracts to handle token lock, unlock, mint, and burn logic. | $6,250     |
| **Backend Relayer (Python)**       | Development of a secure, event-driven backend service for cross-chain event monitoring, validation, and message relaying. | $6,250     |
| **Frontend (Next.js + Tailwind)** | Creation of a responsive user interface with wallet integrations (Phantom and Metamask Snap) enabling seamless swaps. | $5,000     |
| **Final Deployment & Audit Prep** | Mainnet deployment, end-to-end integration testing, documentation, and preparation for third-party security audits. | $7,500     |
| **Total**                        |                                                     | **$25,000** |

---

## 📆 Milestones

### 🧱 Milestone 1: Smart Contract Development (25%) — **$6,250**

- Develop and deploy core smart contracts on Qubic and Solana testnets.
- Implement locking and unlocking logic on Qubic.
- Implement minting and burning logic on Solana for wrapped tokens.
- Perform initial functional testing of cross-chain token flow.

---

### 🔁 Milestone 2: Backend Relayer Development (25%) — **$6,250**

- Build a Python backend service to monitor blockchain events in real-time.
- Implement robust validation, nonce management, and replay protection.
- Develop APIs to expose transaction statuses and swap information.
- Integrate backend with smart contracts for seamless relay operation.

---

### 🖥 Milestone 3: Frontend Development (20%) — **$5,000**

- Create a user-friendly, responsive frontend with Next.js and Tailwind CSS.
- Integrate wallet connections: Phantom (Solana) and Metamask Snap (Qubic).
- Develop UI for selecting swap directions, entering amounts, and tracking status.
- Connect frontend to backend APIs for dynamic updates.

---

### 🚀 Milestone 4: Deployment, Integration & Audit (30%) — **$7,500**

- Deploy all components to mainnets and finalize integration.
- Conduct comprehensive end-to-end testing of the full system.
- Deliver detailed user and developer documentation.
- Prepare codebase and environment for third-party security audit.

---

## 📝 Final Notes

- The Qubic wallet integration will leverage **Metamask Snap**, pending confirmation from the Qubic team regarding compatibility and user adoption.
- Security is a priority; a third-party audit by a reputable firm is strongly recommended before any mainnet launch to ensure code robustness and safeguard user assets.
- The architecture will be designed for modularity and scalability, enabling future enhancements such as liquidity management, fee distribution mechanisms, and multi-chain expansion.
- Ongoing maintenance, monitoring, and operational support post-launch can be scoped separately as needed.

