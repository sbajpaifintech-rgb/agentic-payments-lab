---
name: agentic-payments-lab
description: "Manages Shrish Bajpai's Agentic Payments Lab: the repo, content, and roadmap. Use this skill ANY time the user is working on agentic payments content: building MCP servers, writing code for payment agents, drafting LinkedIn posts, writing protocol explainers, creating PRDs or architecture docs, or doing anything related to the agentic-payments-lab repo. Also trigger when the user mentions any of: MCP payments, ADK orchestrator, AP2, TAP, Verifiable Intent, UCP, cross-border agent, treasury agent, protocol deep-dive, payment API design, LinkedIn post about payments, or any roadmap phase. This skill automatically handles folder creation, README generation, template application, repo structure updates, and voice/tone consistency so the user never has to think about project scaffolding."
---

# Agentic Payments Lab : Project Skill

You are helping Shrish Bajpai build the Agentic Payments Lab. This skill ensures the repo evolves correctly as work progresses: folders appear when needed, READMEs are populated, templates are applied, and everything stays consistent with the roadmap and voice guide.

## The Big Picture

The 7 projects in this repo explore one question: **what does payment infrastructure look like when AI agents are the primary consumer?**

Payments don't exist for their own sake. They serve use cases. Those use cases are becoming agentic. Google built AP2, Visa built TAP, Mastercard built Verifiable Intent, and Anthropic's MCP is now adopted by every major AI lab. These protocols exist because payment networks recognize that the entity initiating payments is shifting from humans to agents, and the existing stack wasn't designed for that.

Projects 01-04 and 06-07 are the payment infrastructure: MCP tools, multi-agent orchestration, protocol implementations, cross-border routing, explainers, and API design. Project 05 (Treasury Agent) is the anchor use case that exercises the full stack. Treasury was chosen because the decision-making layer is genuinely non-deterministic (cash positioning, FX hedging, liquidity forecasting across entities), which creates a strong test of where agents add real value above the payment layer.

The anchor scenario: A corporate treasurer's AI agent wakes up to GBP receivables arriving next week (probabilistic), SGD payroll due Friday (fixed), a supplier in Lagos waiting on $10K (flexible timing), and cash scattered across entities in Singapore, London, and Delaware. The treasury agent reasons about the decisions. The payment infrastructure underneath executes them.

Read `unified_narrative` and `build_philosophy` in `references/project-registry.json` for the full mapping.

**Build philosophy:** Impressive demos. The payment infrastructure projects should feel production-grade. The treasury use case should show both the deterministic path (payment execution) and the non-deterministic path (treasury reasoning) to make clear where agents add value. Hit real APIs where possible (Alpha Vantage for FX, Plaid sandbox for accounts, public OFAC sanctions lists). Mock payment execution and treasury data (multi-entity positions, cash flow forecasts).

## How This Skill Works

Whenever the user starts work on any part of the roadmap, you handle the scaffolding automatically : no explicit instructions needed. The user says "let's build the MCP payments server" or "draft the AP2 explainer" and you:

1. Check the current repo state (what folders exist already)
2. Create the right project folder if it doesn't exist
3. Apply the correct template(s) for companion docs
4. Generate a project-specific README
5. Update the root README.md to list the new project
6. Apply the tone & voice guide to all written content
7. After completing work, remind the user to commit and push

## Step 1: Always Read These First

Before doing ANY work, read these files from the user's workspace (`agentic-payments-lab/`):

1. **`TONE-AND-VOICE-GUIDE.md`** : Voice rules for all content. Every word you write must follow this.
2. **The roadmap** : Read `Agentic_Payments_Roadmap.md` (in the parent `Agentic Payments/` folder) to understand the full plan and where the current task fits.
3. **`references/project-registry.json`** in this skill's directory : The source of truth for project specs (folder names, files, companion docs, templates to use).

Then check the current repo state:
```bash
ls agentic-payments-lab/
```

This tells you what projects already exist so you know what to create vs. skip.

## Step 2: Identify the Project

Match the user's request to a project in `references/project-registry.json`. Each project has:
- `id` : the folder name (e.g., `01-mcp-payments-server`)
- `name` : human-readable name
- `phase` : which roadmap phase it belongs to
- `folder_structure` : exact subdirectories and files to create
- `companion_docs` : which docs to create and which template to use
- `readme_spec` : what the project README should contain
- `triggers` : keywords that indicate the user is working on this project

If the user's request doesn't clearly map to one project, ask which one they mean.

## Step 3: Scaffold the Project Folder

If the project folder doesn't exist yet:

1. Create the folder and all subdirectories from `folder_structure`
2. Create placeholder Python files with module docstrings (not empty `touch` files : each should have a docstring explaining its purpose)
3. Create the project README using the `readme_spec`
4. Create companion doc files by reading the corresponding template from `agentic-payments-lab/templates/` and populating the metadata (title, author, date) : leave the body sections as template placeholders for later

If the project folder already exists, skip to doing the actual work the user asked for.

## Step 4: Update the Root README

After creating a new project folder, update `agentic-payments-lab/README.md`:

1. Read the current README
2. Find the "What's Coming" section
3. Move the relevant bullet from "What's Coming" into a new "Projects" table (create it if it doesn't exist yet)
4. The Projects table format:

```markdown
## Projects

| # | Project | What It Demonstrates | Status |
|---|---------|---------------------|--------|
| 01 | [MCP Payments Server](./01-mcp-payments-server/) | Payment operations as MCP tools for any AI agent | 🟡 In progress |
```

Use these status markers:
- 🟡 In progress : actively being built
- ✅ Complete : shipped with working code and docs

When a project is done, update its status to ✅.

## Step 5: Do the Actual Work

Now do what the user actually asked for : write code, draft content, build the agent, whatever. Throughout:

- **Apply the voice guide** to all written content (LinkedIn posts, docs, READMEs, code comments)
- **Use the correct template** for any companion docs (PRD, architecture doc, protocol explainer, vision doc)
- **Write meaningful Python files** : not empty placeholders. If building a tool, include the function signature, docstring, and basic structure even if the implementation is stubbed

## Step 6: Post-Work Reminders

After completing work, remind the user:
- "This is ready to commit and push" (but don't run git commands unless asked)
- If this was a new project folder, mention that the root README has been updated
- If there's a natural next step on the roadmap, mention it

---

## Content Creation Rules

### LinkedIn Posts
When the user asks to draft a LinkedIn post:
1. Read `TONE-AND-VOICE-GUIDE.md` and `templates/LINKEDIN-POST-TEMPLATE.md`
2. Follow the hook → context → insight → evidence → takeaway → question structure
3. Keep to 150-300 words
4. Output the draft, suggested visual, suggested tags, and 2-3 alternative hooks
5. Never mention JPMorgan in any official capacity
6. End with hashtags: #AgenticPayments #MCP #AI #Payments #Fintech #AgentDevelopment

### Protocol Explainers
When the user asks to write a protocol explainer:
1. Read `TONE-AND-VOICE-GUIDE.md` and `templates/PROTOCOL-EXPLAINER-TEMPLATE.md`
2. Search the web for the latest spec/announcements (these protocols change fast)
3. Follow the template structure exactly: What It Is → Problem → How It Works → Technical Details → Coverage → Maturity → Assessment → Reading
4. Always include an ASCII flow diagram and a maturity assessment table
5. Save to `06-protocol-deep-dives/` (creating the folder if needed)

### PRDs, Architecture Docs, Vision Docs
When the user asks to write any companion doc:
1. Read `TONE-AND-VOICE-GUIDE.md` and the corresponding template from `templates/`
2. Populate metadata (title, author, date)
3. Fill in as much substance as possible based on the project context and roadmap
4. Save to the correct project folder

---

## Voice Quick Reference

These principles apply to EVERYTHING you write (code comments, READMEs, docs, posts):

- **Lead with substance, not credentials**
- **Builder energy:** "I built this" not "I read about this"
- **Product-minded:** connect technical details to user problems and commercial implications
- **Specific and concrete:** real numbers, real protocol names, real corridors
- **Confident but intellectually honest:** acknowledge what's V0.1 and untested
- **Never speak for JPMorgan** or reference proprietary systems
- **Never use em dashes (the long dash character).** Use commas, semicolons, colons, periods, or parentheses instead.
- **Never include meta-commentary.** No sentences about why a section matters, how impactful an artifact is, or instructions to the reader about the document itself. Just deliver the content.
