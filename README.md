# Agentic Payments Lab

When the entity initiating a payment is an AI agent instead of a human clicking buttons, what needs to change in payment infrastructure?

**By [Shrish Bajpai](https://linkedin.com/in/shrishbajpai)** | 15 years building payment platforms at scale.

---

## What I'm Exploring

Payments don't exist for their own sake. They serve use cases. And those use cases are becoming agentic.

Google launched AP2. Visa launched TAP. Mastercard open-sourced Verifiable Intent. Anthropic's MCP is now adopted by every major AI lab. These aren't science projects. Payment networks are retooling their protocols because the consumer of payment services is shifting from humans to AI agents, and the existing infrastructure wasn't designed for that.

An agent can't click "Confirm Payment." It needs cryptographic authorization with scoped constraints. An agent doesn't have a session cookie. It needs verifiable identity and attestation. An agent operating across six entities and fifteen currencies doesn't make one payment decision at a time. It reasons over cash positions, FX exposure, and liquidity forecasts, then issues a batch of payment instructions that the infrastructure must execute reliably.

This repo explores what payment infrastructure looks like when agents are the primary consumer. Treasury management is the anchor use case: the decision-making is genuinely non-deterministic (that's why full-time treasurers still exist), which makes it a strong test of where agents add real value. But the core work is the payment stack underneath.

## The Agentic Payments Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                    USE CASE LAYER (Agent)                        │
│   Treasury: cash positioning, FX strategy, liquidity forecasting │
│   The non-deterministic decisions that drive payment needs        │
│   Built with: Google ADK, LangChain, Claude Agent SDK            │
└──────────────────────────┬──────────────────────────────────────┘
                           │ payment instructions
┌──────────────────────────▼──────────────────────────────────────┐
│               TRUST & AUTHORIZATION LAYER                        │
│   Google AP2: Intent Mandate, Cart Mandate, Payment Mandate      │
│   Mastercard Verifiable Intent: Cryptographic authorization      │
│   Visa TAP: HTTP Message Signatures, agent attestation           │
└──────────────────────────┬──────────────────────────────────────┘
                           │ authorized instructions
┌──────────────────────────▼──────────────────────────────────────┐
│               PAYMENT INFRASTRUCTURE LAYER                       │
│   MCP server: payment operations as agent-callable tools         │
│   Orchestration: multi-rail routing, corridor optimization       │
│   Compliance: sanctions screening, KYC/KYA, regulatory checks    │
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

- **MCP Payments Server**: Payment operations exposed as MCP tools for any AI agent
- **ADK Payment Orchestrator**: Multi-agent payment orchestration with Google ADK
- **AP2 / TAP / Verifiable Intent**: Reference implementations of agentic payment protocols
- **Cross-Border Routing**: Multi-rail corridor optimization (SWIFT, stablecoins, mobile money)
- **Treasury Agent**: The anchor use case, an agent that reasons about cash positioning, FX, and liquidity, then drives payments
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
