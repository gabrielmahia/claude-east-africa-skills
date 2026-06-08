# Skill: East Africa AI Stack Architecture

## Purpose
Explains the complete East Africa AI Stack architecture so Claude can reason
about how tools fit together, recommend the right tool for a task, and
extend the stack correctly.

## Load this skill when:
- Building new tools for East Africa
- Integrating existing tools
- Recommending the right tool for a use case
- Understanding the MCP/A2A/ADK layer

---

## Stack Overview

```
Layer 4: Applications (Streamlit, CLI, Web)
├── shamba-scan-ai (crop disease)
├── afya-chw-ai (CHW clinical support)
├── haki-debate-ai (constitutional rights)
├── kenya-nowcast (economic tracker)
├── quantum-maestro (options trading)
└── 30+ other Streamlit apps

Layer 3: Agent Protocols
├── MCP (Model Context Protocol)
│   ├── mpesa-mcp (22 tools, PyPI v0.2.0)
│   ├── wapimaji-mcp (3 tools, water/drought)
│   ├── civic-agent-kit (6 tools, civic data)
│   ├── remit-mcp (3 tools, remittance)
│   └── swahili-health-mcp (health data)
├── A2A (Agent-to-Agent)
│   └── kenya-a2a (first in East Africa)
└── Google ADK
    └── kenya-adk (first in East Africa)

Layer 2: Data & Models
├── RAG: kenya-legal-rag (LlamaIndex)
├── Datasets: swahili-civic-nlp, kenya-agricultural-qa,
│            kenya-legal-nlp, swahili-health-corpus
└── Agents: hesabu-agent (CrewAI), kenya-3d (Blender MCP)

Layer 1: APIs & Infrastructure
├── Safaricom Daraja (M-PESA)
├── Africa's Talking (SMS, Airtime)
├── Google Gemini (AI, Vision, Flash)
├── NDMA (drought data)
├── Kenya Parliament API
└── yfinance, World Bank RPW
```

---

## When to Use Which Layer

**Use an MCP server when:**
- An AI agent (Claude, GPT-4, Gemini) needs to call an external API
- You want tool-calling without custom integrations
- The operation is repeatable and well-defined

**Use a Streamlit app when:**
- Non-technical users need to interact with AI
- The output is visual/formatted
- Mobile-first access is needed
- Demo/proof-of-concept for a new tool

**Use the RAG layer when:**
- Querying large document corpora (legal texts, health guidelines)
- Semantic search over structured knowledge
- Building Q&A systems over Kenya-specific data

**Use the A2A/ADK layer when:**
- Multiple AI agents need to coordinate
- Complex multi-step tasks require orchestration
- You need agent-to-agent communication

---

## Extension Patterns

### Adding a new MCP tool to mpesa-mcp:
```python
@mcp.tool(annotations={"readOnlyHint": False, "destructiveHint": True})
def mpesa_new_tool(param: Annotated[str, "Description"]) -> dict:
    # 1. Validate input
    # 2. Build Daraja request
    # 3. Call _daraja_post(endpoint, payload)
    # 4. Audit: _audit("mpesa_new_tool", {"param": param}, "RESULT")
    # 5. Return structured dict
    pass
```

### Adding a new Streamlit app:
```python
# Template: standard pattern across all apps
API_KEY = st.secrets.get("GOOGLE_API_KEY") or st.secrets.get("GEMINI_API_KEY", "")
if not API_KEY:
    st.warning("⚠️ Huduma hii bado haijaungwa. / Service not yet configured.")
    st.stop()
```

### Trust Integrity Rules (mandatory):
- DEMO/synthetic data: label with "DEMO — Synthetic data. Source: [description]"
- No implied real institutional partnerships
- No operational recommendations from demo models
- All financial tools: "Not financial advice"

---

## Deployment Architecture

**Streamlit apps:** Streamlit Cloud (free tier)
  - Each app: separate GitHub repo
  - Secrets: GOOGLE_API_KEY or GEMINI_API_KEY (+ TRADIER_TOKEN for Quantum Maestro)
  - Mobile-first: 44px+ tap targets, 16px+ fonts, single-column base

**MCP servers:** PyPI packages + stdio transport
  - Install: pip install [package-name]
  - Run: [package-name] (CLI entry point)
  - Glama registry: glama.ai/mcp/servers/gabrielmahia/[name]

**Datasets:** HuggingFace (gmahia)
  - License: cc-by-4.0
  - All include research context sections (arXiv citations)

---

## Portfolio Statistics (June 2026)
- 115+ GitHub repos
- 4 MCP servers on PyPI
- 5 HuggingFace datasets
- 400+ PyPI downloads, 12 countries
- 3 protocol firsts (MCP, A2A, ADK) — first in East Africa
- 5 arXiv/IMF/WHO research-backed implementations
- 7 Dev.to articles
- 5 Kaggle notebooks

---
*© 2026 AI Kung Fu LLC · MIT License · claude-east-africa-skills*
