# FlashDrop ⚡️

> **Zero-Collateral Instant Liquidity Protocol on Stellar**

FlashDrop is a high-performance flash loan provider built on [Soroban](https://soroban.stellar.org/). It enables anyone to borrow millions in assets with **zero upfront collateral** — as long as the principal and a small fee are returned within the same atomic transaction.

---

## Table of Contents

- How It Works
- Key Features
- Project Structure
- Getting Started
  - Prerequisites
  - Installation
- License

---

## How It Works

FlashDrop exploits the **atomicity** of the Stellar network: a transaction either succeeds entirely or fails entirely — there is no in-between.

```
1. Borrow  →  Your contract receives 100,000 USDC from FlashDrop.
2. Execute →  Your contract performs arbitrage or a liquidation on another DEX.
3. Repay   →  Your contract returns 100,000 USDC + 0.05% fee to FlashDrop.
```

> **If step 3 fails**, the network automatically reverts steps 1 and 2. FlashDrop never loses funds — the atomicity guarantee *is* the security model.

---

## Key Features

| Feature | Description |
|---|---|
| ⚡️ **Zero-Collateral Borrowing** | Access deep liquidity for arbitrage, collateral swapping, or liquidations without owning the underlying assets. |
| 🔒 **Atomic Security** | Repayment is enforced at the network level. If a loan isn't repaid, the entire transaction reverts. |
| 🧩 **Developer SDK** | Modular `borrower_interface` trait lets Soroban developers integrate Flash-Actions into their own contracts in minutes. |
| 💸 **Ultra-Low Fees** | Flat **0.05% fee** on all loans — lower than traditional on-chain lending markets. |

---

## Project Structure

```
flash-drop/
├── contracts/
│   ├── pool/                  # Core vault — where LPs deposit funds
│   ├── borrower_interface/    # Trait external contracts must implement to receive a loan
│   └── examples/              # Sample Arbitrageur contracts to get started quickly
├── frontend/                  # Liquidity Portal — deposit assets & track fee earnings
├── backend/                   # Arbitrage Monitor — scans Stellar DEXs for price discrepancies
└── LICENSE
```

---

## Getting Started

### Prerequisites

Ensure the following tools are installed before building:

| Tool | Version |
|---|---|
| [Rust](https://rustup.rs/) | `v1.84.0+` |
| [Stellar CLI](https://developers.stellar.org/docs/tools/developer-tools/cli/stellar-cli) | `v22.0.0+` |
| [Docker](https://www.docker.com/) | Latest (used to run a local Soroban RPC node) |

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/flash-drop.git
cd flash-drop
```

**2. Build the Soroban contracts**

```bash
cargo build --target wasm32-unknown-unknown --release
```

**3. Run the simulation**

A ready-to-run mock arbitrage script is included in `contracts/examples/`. Follow the instructions inside that directory to execute a simulated flash loan against a local Stellar network.

---

## License

Distributed under the **MIT License**. See [`LICENSE`](./LICENSE) for details.
