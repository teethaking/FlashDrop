# Contributing to FlashDrop ⚡️

FlashDrop is a foundational DeFi primitive. Because we handle large amounts of uncollateralized liquidity, security and code quality are our top priorities.

---

## 🚦 The Contribution Workflow

### 1. The "Issue-First" Rule
We do not accept unsolicited Pull Requests.
* Find a Task: Check the [Issues] tab for [Contract], [Frontend], or [Backend] tasks.
* Get Assigned: Comment on the issue to be assigned.
* Claim Initialization: If you are the first to work on a module, follow the [Initialization Template] to set up the folder structure.

### 2. Technical Guidelines

#### 🦀 Contracts (/contracts)
* Atomic Checks: Every flash loan function must end with a balance check to ensure repayment.
* Re-entrancy Protection: Use the storage().instance() to manage re-entrancy guards during a loan execution.
* Events: Every loan must emit a flash_loan_executed event containing the amount, asset, and fee paid.

#### ⚛️ Frontend (/frontend)
* Real-time Data: Use subscriptions to track pool liquidity and current fee earnings.
* Simulator: Help build the "Flash Loan Simulator" UI where developers can test their logic before deploying.

#### 🗄 Backend (/backend)
* Performance: The backend must handle high-concurrency event monitoring without dropping ledger entries.
* Integrations: Build connectors for popular Stellar DEXs (Soroswap, Phoenix, etc.).

---

## 📂 PR Requirements

1. Tests are Mandatory: No contract PR will be merged without 100% pass rate on cargo test.
2. Documentation: Any new public function must be documented in the code using ///.
3. Formatting: Run cargo fmt and npm run lint before committing.

---

## 🛡 Security First
If you find a potential exploit in the flash loan logic, do not open a public issue. Please contact the maintainers directly via the "Security" tab on GitHub.

Let's build the fastest liquidity in the galaxy! 🚀
