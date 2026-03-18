# Agentic Payments Lab

Payment infrastructure for agent-initiated transactions: MCP tools, multi-agent orchestration, protocol implementations (AP2, TAP, Verifiable Intent), and cross-border routing. Treasury management as the anchor use case.

**[Shrish Bajpai](https://linkedin.com/in/shrishbajpai)**

---

## What I'm Building

An MCP server that exposes payment operations (transfers, FX rates, sanctions screening) as tools for AI agents. A multi-agent orchestrator using Google ADK to coordinate compliance, routing, and settlement. Reference implementations of AP2, TAP, and Verifiable Intent (the protocols Google, Visa, and Mastercard built for agent-initiated payments). A cross-border routing engine that evaluates SWIFT vs stablecoins vs mobile money vs instant rails for a given corridor. And a treasury agent that ties it all together: reasoning about cash positions across six entities, FX exposure in fifteen currencies, and liquidity forecasts that change daily, then pushing payment instructions into the stack below.

Treasury is the anchor use case. The decision-making there is genuinely non-deterministic (cash positioning, FX hedging, funding source selection across jurisdictions), which is why full-time treasurers still exist and why it makes a good test of where agents earn their keep.

## The Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                    USE CASE LAYER (Agent)                        │
│   Treasury: cash positioning, FX strategy, liquidity forecasting │
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
└──────────────────────────┬──────────────────────────────────────┘
                           │ execution
┌──────────────────────────▼──────────────────────────────────────┐
│                   PAYMENT RAILS LAYER                            │
│   Cards (Visa/MC), Instant Rails (FedNow/UPI/FPS),              │
│   SWIFT, Stablecoins (USDC/USDT), Mobile Money                  │
└─────────────────────────────────────────────────────────────────┘
```

## Projects

- **MCP Payments Server**: Six payment tools (initiate_transfer, check_status, get_fx_rate, screen_sanctions, categorize_transaction, reconcile_batch) exposed via MCP
- **ADK Payment Orchestrator**: Google ADK multi-agent system with compliance, routing, FX, and settlement sub-agents
- **AP2 / TAP / Verifiable Intent**: Reference implementations of all three agentic payment protocols, plus a comparison matrix
- **Cross-Border Routing**: Corridor optimizer across SWIFT, USDC, M-Pesa, and instant rails (FedNow, UPI, FPS, PIX)
- **Treasury Agent**: Cash positioning, FX exposure, and liquidity forecasting across entities, driving payments through the infrastructure above
- **Protocol Deep-Dives**: PM-level explainers for the full protocol landscape
- **Payment API Design**: OpenAPI specs, error taxonomies, webhook reliability patterns, SDK samples

Each will ship with working code, architecture docs, and companion analysis.

## Setup

```bash
git clone https://github.com/shrishb/agentic-payments-lab.git
cd agentic-payments-lab
cp .env.example .env
# Add your API keys (Alpha Vantage, Plaid sandbox, Anthropic, Google, OpenAI)
```

## License

MIT
