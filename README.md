# Agentic Payments Lab

An AI treasury agent that reasons about cash positioning, FX exposure, and liquidity across entities, then executes payments through protocol-compliant infrastructure.

**By [Shrish Bajpai](https://linkedin.com/in/shrishbajpai)** | 15 years building payment platforms at scale.

---

## The Core Thesis

Payment execution is deterministic: send X to Y via Z. If that were the whole problem, microservices and orchestrators would have solved it years ago (and largely have).

Treasury management is not deterministic. Cash positioning across jurisdictions, FX hedging timing, liquidity forecasting over noisy receivables, funding source selection with tax and covenant constraints: these decisions keep full-time treasurers employed at every multinational. The agent earns its inference cost here, not in the payment plumbing.

This repo builds both layers and draws a clear line between them.

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                 TREASURY REASONING LAYER (Agent)                │
│   Cash positioning, FX strategy, liquidity forecasting,         │
│   funding decisions across multi-jurisdictional entities         │
│   Built with: Google ADK, LangChain, Claude Agent SDK           │
└──────────────────────────┬──────────────────────────────────────┘
                           │ decisions
┌──────────────────────────▼──────────────────────────────────────┐
│              TRUST & AUTHORIZATION LAYER                         │
│   Google AP2: Intent/Cart/Payment Mandates                       │
│   Visa TAP: HTTP Message Signatures, agent attestation           │
│   Mastercard Verifiable Intent: Cryptographic authorization      │
└──────────────────────────┬──────────────────────────────────────┘
                           │ authorized instructions
┌──────────────────────────▼──────────────────────────────────────┐
│            DETERMINISTIC EXECUTION LAYER (MCP Tools)             │
│   Payment initiation, FX conversion, sanctions screening,        │
│   corridor routing, status tracking, reconciliation              │
│   Connected via: MCP (tools, resources, prompts)                 │
└──────────────────────────┬──────────────────────────────────────┘
                           │ execution
┌──────────────────────────▼──────────────────────────────────────┐
│                   PAYMENT RAILS LAYER                            │
│   Cards (Visa/MC), Instant Rails (FedNow/UPI/FPS),              │
│   SWIFT, Stablecoins (USDC/USDT), Mobile Money                  │
└─────────────────────────────────────────────────────────────────┘
```

## What's Coming

This repo will grow as I work through each layer of the stack:

- **Treasury Agent**: The core reasoning agent for cash positioning, FX strategy, and funding decisions
- **MCP Payments Server**: Deterministic payment operations exposed as MCP tools
- **ADK Treasury Orchestrator**: Multi-agent treasury reasoning with Google ADK
- **AP2 / TAP / Verifiable Intent**: Reference implementations of agentic payment protocols
- **Cross-Border Routing**: Multi-rail corridor optimization (SWIFT, stablecoins, mobile money)
- **Protocol Deep-Dives**: PM-level explainers for the full protocol landscape
- **Payment API Design**: Production-grade specs and design patterns

Each project ships when it's ready, with working code, architecture docs, and companion analysis.

## Setup

```bash
git clone https://github.com/shrishb/agentic-payments-lab.git
cd agentic-payments-lab
cp .env.example .env
# Fill in your API keys
```

## License

MIT
