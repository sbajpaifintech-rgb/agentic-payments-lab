# Agentic Payments Lab

Exploring the intersection of AI agents and payment infrastructure through working code, protocol implementations, and opinionated analysis.

**By [Shrish Bajpai](https://linkedin.com/in/shrishbajpai)** | 15 years building payment platforms at scale.

---

## The Agentic Payments Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                    CONSUMER / USER LAYER                        │
│   Consumer grants authority → AI Agent acts on their behalf     │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                    AGENT LAYER                                  │
│   Built with: Google ADK, Claude Agent SDK, LangChain           │
│   Connected via: MCP (tools, resources, prompts)                │
│   Identity: Visa TAP (agent attestation), KYA protocols         │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│               TRUST & AUTHORIZATION LAYER                       │
│   Google AP2: Intent Mandate, Cart Mandate, Payment Mandate     │
│   Mastercard Verifiable Intent: Cryptographic authorization     │
│   Visa TAP: HTTP Message Signatures, merchant verification      │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│               COMMERCE ORCHESTRATION LAYER                      │
│   Google UCP: Discovery → Cart → Checkout → Post-purchase       │
│   Payment Orchestration: Multi-rail routing, settlement         │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│                   PAYMENT RAILS LAYER                           │
│   Cards (Visa/MC), Instant Rails (FedNow/UPI/FPS),             │
│   SWIFT, Stablecoins (USDC/USDT), Mobile Money                 │
└─────────────────────────────────────────────────────────────────┘
```

## Why This Exists

The agentic payments space went from theoretical to production in the last 6 months. Google launched AP2 and UCP. Visa launched TAP. Mastercard open-sourced Verifiable Intent. MCP is now adopted by every major AI lab. But almost no one is building at the intersection of these protocols with real payment infrastructure experience.

This repo is that intersection, and it's being built in the open, one project at a time.

## What's Coming

This repo will grow as I work through each layer of the stack:

- **MCP Payments Server**: Payment operations as tools for any AI agent
- **ADK Payment Orchestrator**: Multi-agent payment orchestration with Google ADK
- **AP2 / TAP / Verifiable Intent**: Reference implementations of agentic payment protocols
- **Cross-Border Agent**: Intelligent multi-rail routing (SWIFT, stablecoins, mobile money)
- **Treasury Agent**: Corporate treasury operations as AI agent tools
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
