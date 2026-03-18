# Setup Checklist: External Tasks

*These are the things you need to do outside of Cowork to get fully operational.*

---

## 1. GitHub Repository

- [ ] Create a new public repo: `agentic-payments-lab` on GitHub
- [ ] Initialize with the folder structure from this workspace (copy the `agentic-payments-lab/` contents)
- [ ] Set default branch to `main`
- [ ] Add repo description: "Building at the intersection of AI agents and payment infrastructure. MCP servers, multi-agent orchestrators, agentic payment protocols (AP2, TAP, Verifiable Intent), and intelligent cross-border routing."
- [ ] Add topics: `agentic-payments`, `mcp`, `ai-agents`, `payments`, `fintech`, `google-adk`, `ap2`, `visa-tap`
- [ ] Verify `.gitignore` is working (no `.env` files committed)
- [ ] Verify CI workflow runs on first push (`.github/workflows/ci.yml`)

## 2. GCP Project Setup

- [ ] Create GCP project: `agentic-payments-lab`
- [ ] Enable APIs:
  - [ ] Cloud Run
  - [ ] Cloud Build
  - [ ] Artifact Registry
  - [ ] Firebase Hosting
  - [ ] Secret Manager
  - [ ] Vertex AI
- [ ] Install Google Cloud CLI locally
- [ ] Install Cloud Code VS Code extension
- [ ] Authenticate: `gcloud auth login`
- [ ] Set project: `gcloud config set project agentic-payments-lab`
- [ ] Create Artifact Registry Docker repository:
  ```bash
  gcloud artifacts repositories create agentic-payments \
    --repository-format=docker \
    --location=us-central1
  ```
- [ ] Set up Cloud Build trigger (GitHub push → auto-deploy to Cloud Run)

## 3. Firebase & Domain

- [ ] Create Firebase project (link to GCP project)
- [ ] Buy custom domain (shrishbajpai.com or similar)
- [ ] Link domain to Firebase Hosting
- [ ] Deploy initial placeholder site: `firebase deploy`

## 4. Secret Manager

- [ ] Store API keys (do NOT commit these to GitHub):
  - [ ] `ANTHROPIC_API_KEY`
  - [ ] `OPENAI_API_KEY`
  - [ ] `GOOGLE_API_KEY`
  - [ ] `ALPHA_VANTAGE_API_KEY`
  - [ ] `PLAID_CLIENT_ID` + `PLAID_SECRET`

## 5. VS Code Extensions

Install these extensions:

- [ ] Python (`ms-python.python`)
- [ ] Jupyter (`ms-toolsai.jupyter`)
- [ ] YAML (`redhat.vscode-yaml`)
- [ ] REST Client (`humao.rest-client`)
- [ ] Docker (`ms-azuretools.vscode-docker`)
- [ ] Google Cloud Code (`googlecloudtools.cloudcode`)
- [ ] Markdown All in One (`yzhang.markdown-all-in-one`)

## 6. Python Environment

```bash
# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\activate on Windows

# Install core dependencies
pip install mcp google-adk anthropic langchain openai
pip install ruff pytest jupyter
pip install requests python-dotenv
```

- [ ] Virtual environment created
- [ ] Core dependencies installed
- [ ] `requirements.txt` updated with pinned versions

## 7. LinkedIn Profile

- [ ] Update headline: "Agentic Payments & AI Infrastructure | Building where AI agents meet payment rails | JPMorgan, Amazon, Citi | LBS MBA"
- [ ] Update About section (lead with the agentic payments thesis, backed by 15 years of payment platform experience)
- [ ] Add "Agentic Payments Lab" as a project with GitHub link
- [ ] Set Creator Mode on (if not already)
- [ ] Follow key accounts: Google ADK, Anthropic, Visa Developer, Mastercard Developers

## 8. Community & Networking

- [ ] Join Google Developer forums (AP2/UCP threads)
- [ ] Join MCP Discord / GitHub discussions
- [ ] Scan LBS alumni network for contacts at Visa, Mastercard, Google, Stripe agentic teams
- [ ] Identify internal stakeholders (manager, skip-level, platform engineering leads) to share work with later

---

## Priority Order

If you're short on time, do these first:

1. **GitHub repo** (everything else builds on this)
2. **VS Code extensions + Python environment** (so you can start building)
3. **LinkedIn profile update** (signals your new direction immediately)
4. **GCP project** (needed before you can deploy anything)
5. **Firebase + domain** (can wait until you have something to host)
6. **Community** (start engaging once you have your first post ready)
