# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Primary user: an individual Solana holder who wants to deposit, hold, and transfer funds privately, without every transaction being publicly traceable on-chain. Their core job is depositing SOL/SPL tokens into the shielded pool, sending private transfers, and withdrawing back out — the Login → Register → Dashboard → Transaction flow.

Secondary role: an auditor/compliance user, served by the separate Auditor page, who verifies transactions via selectively-shared encrypted disclosure receipts rather than by seeing the whole chain.

## Product Purpose

CipherPay is a privacy-preserving payment platform built on Solana. It shields balances and transfers using zero-knowledge proofs (Groth16), commitments, and nullifiers so transaction details aren't publicly linkable, while still letting a user selectively prove a transaction to an authorized auditor.

## Positioning

Auditable privacy: transactions are private by default, but selectively provable to a designated auditor via end-to-end-encrypted disclosure receipts. This is the meaningful difference from typical privacy coins/mixers, which offer privacy with no compliance path — CipherPay's privacy is not a compliance dead-end.

## Operating Context

- Solana wallet-based flow (wallet-adapter): connect wallet, register/login, then operate from a Dashboard.
- Core actions: deposit into the shielded pool, transfer privately between users (with recipient lookup), withdraw out, and approve a relayer delegate (gasless/relayed transaction execution).
- Proof generation (ZK) is a distinct step/page in the flow, separate from the transaction itself.
- Auditor role is a separate page/flow: compares ciphertext and audits, decrypts audit receipts (e2ee) shared by a user.
- A companion app, zkaudit-ui, shares session state with this app cross-origin via postMessage.

## Capabilities and Constraints

- Solana-only; no multi-chain support. Design and product work should not assume other chains.
- SPL token support (via @solana/spl-token) alongside native SOL.
- Pre-production / testnet stage: current workflows (README) are airdrop/localhost-oriented, not yet a polished production consumer app.
- Terminology: shielded "notes" (spendable notes, withdrawable notes), commitments, nullifiers, relayer delegate, disclosure/audit receipt.
- Relayer delegate approval is a distinct, explicit user action (approve a spend delegate for relayed/gasless transactions).

## Evidence on Hand

- No confirmed brand assets (logo, color system, typography) beyond the product name "CipherPay" — visual identity is open.
- No testimonials, case studies, press, or production usage data on hand; do not fabricate any.

## Product Principles

- Privacy is the default state of every balance and transfer, not an opt-in mode.
- Privacy must remain provable on demand — the product never trades away the audit path for stronger secrecy.
- Every private action (deposit, transfer, withdraw, delegate approval) is an explicit, distinct user step — never bundled or hidden behind a generic "confirm."
- Solana-native: design and performance assumptions are scoped to Solana, not a generic multi-chain wallet experience.
- The product is early-stage; flows should read as trustworthy and legible before they read as polished.
