# nexus-treasury-agent
Autonomous AI treasury agent built on Tether WDK. Evaluates contractor deliverables and settles USDT₮ payments onchain across Ethereum, TON, Solana, and Tron — no human required at execution time. Self-custodial, multi-chain, zero third-party custody. Built for Tether Hackathon Galactica: WDK Edition 1.
# NEXUS — Autonomous Treasury Agent

> Autonomous AI treasury agent built on Tether WDK. Evaluates contractor deliverables and settles USDT₮ payments onchain across Ethereum, TON, Solana, and Tron — no human required at execution time.

![NEXUS Banner](./assets/nexus-logo.jpg)

[![Built with WDK](https://img.shields.io/badge/Built%20with-Tether%20WDK-00d283?style=flat-square)](https://docs.wdk.tether.io)
[![Hackathon](https://img.shields.io/badge/Tether%20Hackathon-Galactica%20WDK%20Edition%201-blue?style=flat-square)](https://dorahacks.io/hackathon/hackathon-galactica-wdk-2026-01/detail)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](./LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-20%2B-339933?style=flat-square)](https://nodejs.org)

---

## The Problem

AI agents today can think, plan, and reason — but they **cannot hold or move money**. Every time an agent needs to pay for a completed task, a human must intervene. This breaks the promise of true autonomy.

Contractor payouts involve invoices, approval chains, bank wires, and days of waiting — all to answer one question: *"Was the work done?"* If that evaluation can be automated, the entire payment pipeline collapses into a single onchain transaction.

**NEXUS solves this.** It gives AI agents a self-custodial wallet, the ability to evaluate deliverables, and the power to settle USDT₮ onchain — autonomously, across multiple chains, with zero third-party custody.

---

## How It Works

```
Operator defines task → Contractor submits deliverable
        ↓
NEXUS evaluates deliverable against spec (AI-powered)
        ↓
Pre-transaction checklist + fee estimation via WDK
        ↓
Operator confirms (explicit human approval for writes)
        ↓
NEXUS signs & broadcasts USDT₮ transfer onchain
        ↓
Contractor wallet receives payment. Task closed.
```

---

## Features

- **Self-custodial multi-chain wallets** — EVM, TON, Solana, Tron, Bitcoin, Spark via Tether WDK
- **AI-powered task evaluation** — agent reviews deliverables against defined specs before releasing funds
- **Autonomous USDT₮ settlement** — signs and broadcasts transfers without human execution bottleneck
- **Gasless support** — fee-free transfers on TON (paymaster) and Tron (gas-free service)
- **Explicit confirmation model** — all write operations require operator sign-off per WDK security guidance
- **Prompt injection protection** — built-in detection rules following WDK agent skill spec
- **Live treasury dashboard** — real-time wallet balances, task queue, agent logs, and settlement flow

---

## Tech Stack

| Layer | Technology |
|---|---|
| Agent Runtime | Node.js + WDK Agent Skills |
| Wallet & Transactions | `@tetherto/wdk-wallet-evm`, `wdk-wallet-ton`, `wdk-wallet-solana`, `wdk-wallet-tron` |
| Swaps | Velora (EVM), StonFi (TON) |
| Bridges | USDT0 via LayerZero |
| Lending | Aave V3 |
| Fiat On/Off-Ramp | MoonPay via WDK Fiat Module |
| Indexer | WDK Indexer API |
| AI Evaluation | Claude (via Anthropic API) |
| Frontend | HTML / CSS / Vanilla JS |

---

## Supported Chains

| Chain | Token | Notes |
|---|---|---|
| Ethereum | USDT₮ (ERC-20) | Primary settlement chain |
| TON | USDT₮ (Jetton) | Gasless via paymaster |
| Solana | USDT₮ (SPL) | High throughput |
| Tron | USDT₮ (TRC-20) | Gasless via gas-free service |
| Bitcoin | BTC | Store of value |
| Spark | USDT₮ | Lightning-fast settlement |

---

## Getting Started

### Prerequisites

- Node.js v20+
- npm v9+
- Anthropic API key (for task evaluation)

### Installation

```bash
git clone https://github.com/your-username/nexus-treasury-agent.git
cd nexus-treasury-agent
npm install
```

### Load the WDK Agent Skill

```bash
npx skills add tetherto/wdk-agent-skills
```

### Configure Environment

```bash
cp .env.example .env
```

Edit `.env`:

```env
ANTHROPIC_API_KEY=your_anthropic_api_key
WDK_NETWORK=mainnet        # or testnet
AGENT_CONFIRM_REQUIRED=true  # always true — explicit confirmation before writes
```

### Run the Agent

```bash
npm run dev
```

The dashboard will be available at `http://localhost:3000`.

---

## Project Structure

```
nexus-treasury-agent/
├── agent/
│   ├── index.js          # Agent entrypoint
│   ├── evaluator.js      # AI-powered task evaluation logic
│   ├── treasury.js       # Multi-chain wallet management via WDK
│   └── settler.js        # Transaction signing and broadcast
├── frontend/
│   └── index.html        # Live treasury dashboard
├── tasks/
│   └── schema.js         # Task and deliverable schema definitions
├── skills/
│   └── SKILL.md          # WDK agent skill file
├── .env.example
├── package.json
└── README.md
```

---

## Security

NEXUS is built with security as a first principle, following WDK's agent security guidance:

- **Self-custodial keys** — private keys never leave your machine, no third-party custody
- **Explicit write confirmation** — every transaction, swap, or bridge requires operator approval before execution
- **Pre-transaction validation** — fee estimation and address verification run before any sign operation
- **Prompt injection detection** — agent skill includes rules to detect and block injection attempts
- **Key cleanup patterns** — mandatory cleanup after each session per WDK skill spec

---

## Roadmap

- [x] Multi-chain wallet creation via WDK
- [x] AI task evaluation engine
- [x] USDT₮ settlement on EVM, TON, Solana, Tron
- [x] Live treasury dashboard
- [ ] Escrow contract support (milestone-based releases)
- [ ] Cross-chain bridge auto-routing (USDT0 via LayerZero)
- [ ] DAO governance integration for multi-sig approvals
- [ ] Aave V3 lending module for idle treasury yield
- [ ] MoonPay fiat on-ramp for operator top-ups

---

## Built For

**Tether Hackathon Galactica: WDK Edition 1**
Hosted on DoraHacks · $30,000 Prize Pool

---

## License

MIT © 2026 NEXUS Contributors
