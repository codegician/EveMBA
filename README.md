# EveMBA — Interstellar Business Academy

> **An AI-powered MBA learning platform embedded inside EVE Frontier.**
> Real business education, triggered by real gameplay.

[![Live Demo](https://img.shields.io/badge/demo-live-c8922a?style=flat-square)](https://codegician.github.io/EveMBA)
[![Built on Sui](https://img.shields.io/badge/blockchain-Sui-4db87a?style=flat-square)](https://sui.io)
[![Powered by Claude](https://img.shields.io/badge/AI-Claude%20Haiku-e8c060?style=flat-square)](https://anthropic.com)

---

## What Is This?

EveMBA bridges the gap between EVE Frontier's emergent economy and real-world business education. When you complete a trade, an MBA lesson on supply and demand fires. When a corp member joins, org theory triggers. When your gate gets attacked, risk management activates.

Every in-game action becomes a personalized case study. Every credential earned in Frontier becomes a verifiable on-chain certificate.

This is the MBA you actually want to do.

---

## The Core Insight

EVE Frontier's player-driven economy is one of the most sophisticated simulations of real-world economics ever built. Players already learn supply chain management, corporate finance, risk management, and competitive strategy — they just don't know it has a name.

EveMBA names it. Teaches it. And certifies it on-chain.

---

## Current Build (v0.1 — Demo)

A fully functional single-page dApp built as a proof of concept for the EVE Frontier ecosystem.

### ✅ Shipped

| Feature | Status |
|---|---|
| EVE Vault wallet connect (Sui Wallet Standard) | ✅ Live |
| AI Business Advisor (Claude Haiku via Cloudflare Worker) | ✅ Live |
| MBA concept-tagging engine (11 game event types → frameworks) | ✅ Live |
| Live activity feed with concept-tagged events | ✅ Live |
| MBA track dashboard (6 tracks with progress) | ✅ Live |
| Curriculum module viewer (5 MBA modules with EVE context) | ✅ Live |
| Certification milestone system with unlock logic | ✅ Live |
| Market intelligence panel with live price simulation | ✅ Live |
| Corp & Org management view | ✅ Live |
| On-chain credentials viewer | ✅ Live |
| Sui GraphQL API layer (character data + event polling) | ✅ Integrated |
| EVE Frontier-aligned visual theme (warm dark / gold) | ✅ Live |

---

## Planned Feature Releases

### Phase 1 — Live Data (v0.2)
> *Connect the demo to real Frontier game state*

- **Real wallet data**: Pull actual ISK balance, trade history, and corp membership from the connected EVE Vault address via Sui GraphQL
- **Live event polling**: Wire `suix_queryEvents` to the world contracts — real trades and actions trigger real MBA lessons
- **Dynamic system prompt**: AI advisor receives actual player metrics instead of demo data
- **Character identity**: Display real pilot name and portrait from on-chain `PlayerProfile`

### Phase 2 — Certification Engine (v0.3)
> *Make credentials real and valuable*

- **On-chain credential minting**: Issue Sui NFT certificates when milestone thresholds are crossed (e.g. 50 trades → "Market Analyst I")
- **Verifiable proof of learning**: Credentials stored on Sui, visible in EVE Vault, portable to any dApp
- **Leaderboard**: Corp-level MBA ranking — which corp produces the most credentialed pilots?
- **Cross-pilot benchmarking**: Compare your MBA progress against the broader Frontier population

### Phase 3 — Smart Assembly Integration (v0.4)
> *Embed MBA lessons directly into in-game structures*

- **Smart Gate MBA terminal**: Attach an EveMBA learning station to any Smart Gate — pilots passing through receive contextual lessons based on current market conditions
- **Market Assembly tutor**: Place an AI advisor node inside a smart market — it explains the economics of every transaction in real time
- **Corp Academy**: A corp-owned Smart Assembly that tracks the MBA progress of all members and unlocks corp-level bonuses for completion milestones

### Phase 4 — AI Advisor Depth (v0.5)
> *From lesson triggers to genuine mentorship*

- **Memory layer**: The AI advisor remembers your full trade history, decision patterns, and past lessons — advice compounds over time
- **Scenario simulation**: "What would happen to your portfolio if Void Cartel blockades Sector 12?" — AI-powered what-if analysis
- **Peer case studies**: Real anonymised player decisions from across Frontier become teaching material for others
- **Corp strategy board**: Multi-player AI session where corp leadership discusses strategy with a shared MBA advisor

### Phase 5 — Full MBA Programme (v1.0)
> *A complete business education disguised as a game*

- **7 full MBA tracks**: Market Analysis, Corporate Finance, Strategy, Supply Chain, Diplomacy, Risk Management, Macroeconomics
- **Structured curriculum**: Each track has prerequisites, quizzes, and a capstone project (executed in-game)
- **Real accreditation pathway**: Partnership with online MBA providers to recognise EveMBA credentials toward actual coursework credit
- **DAO governance**: EveMBA credential holders vote on curriculum updates, new tracks, and partnership decisions

---

## Architecture

```
EVE Frontier (Sui blockchain)
        │
        ▼
Sui GraphQL / suix_queryEvents
        │
        ▼
MBA Concept-Tagging Engine          ←── MBA_CONCEPT_MAP (11 event types)
        │                                    │
        ▼                                    ▼
Activity Feed + Toast Notifications    Lesson Triggers
        │
        ▼
Claude Haiku (via Cloudflare Worker)  ←── Real player context
        │
        ▼
EveMBA Dashboard (single-file HTML dApp)
        │
        ▼
On-chain Credential Minting (Sui NFT)
```

**Stack:**
- **Frontend**: Vanilla HTML/CSS/JS — single file, zero dependencies, deployable anywhere
- **AI**: Claude Haiku via Anthropic API, proxied through a Cloudflare Worker
- **Blockchain**: Sui testnet — EVE Vault (Sui Wallet Standard) for identity
- **API**: Sui GraphQL (`graphql.testnet.sui.io`) + JSON-RPC event polling
- **Hosting**: GitHub Pages

---

## MBA Concept Map

The core of EveMBA is a JSON config that maps every significant EVE Frontier game event to a real MBA framework:

| Game Event | MBA Framework | Lesson |
|---|---|---|
| Trade completed | Supply & Demand / Price Discovery | Arbitrage module |
| Arbitrage opportunity detected | Market Efficiency | Arbitrage module |
| Corp member joined | Organizational Theory / Dunbar's Number | Org design |
| Corp member left | Retention Architecture | Incentive design |
| Contract signed | Contract Theory / Principal-Agent | Corp finance |
| Risk alert triggered | Value at Risk / Operational Risk | Risk management |
| Gate attacked | Scenario Analysis / Hedging | Risk management |
| Shipment delivered | JIT Logistics / Network Throughput | Supply chain |
| Trade route established | Network Design / Supply Chain Resilience | Supply chain |
| Price spike detected | Market Microstructure / Demand-Pull | Market analysis |
| Competitive threat | Porter's Five Forces | Strategy |

---

## Running Locally

```bash
# Clone
git clone https://github.com/codegician/EveMBA.git
cd EveMBA

# Open directly in browser — no build step needed
open index.html

# Or serve locally
npx serve .
```

**To enable the AI advisor**, deploy the Cloudflare Worker:
1. Go to [workers.cloudflare.com](https://workers.cloudflare.com)
2. Create a worker and paste `worker.js`
3. Add secret: `ANTHROPIC_API_KEY` = your Anthropic API key
4. Update `WORKER_URL` in `index.html` with your worker URL

**To enable live game data**, update `EVE_FRONTIER_CONFIG` in `index.html`:
```js
worldPackageId: '0x<YOUR_WORLD_PACKAGE_ID>',
```
Get the package ID from [evefrontier/world-contracts](https://github.com/evefrontier/world-contracts).

---

## Wallet Setup

EveMBA uses the **Sui Wallet Standard** — EVE Frontier's official wallet protocol.

1. Install [EVE Vault](https://github.com/evefrontier/evevault) Chrome extension
2. Create your wallet (no seed phrases — uses zkLogin)
3. Click **Connect EVE Vault** on the EveMBA landing screen

Demo mode is available without a wallet.

---

## Why EVE Frontier?

EVE Frontier's player-driven economy is already a graduate-level business simulation. Pilots manage supply chains, negotiate contracts, hedge currency risk, and execute competitive strategy at a level most business schools only theorise about.

The problem is: most players don't know what they're doing has a name.

EveMBA gives it a name. And then gives you a credential for it.

---

*Built for the EVE Frontier ecosystem. Powered by Claude. Runs on Sui.*
