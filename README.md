# Advisors

Advisors is an AI‑assisted, multi‑agent app that coordinates domain specialists (entrepreneurship, NFL fantasy, personal finance, legal, software, design, marketing, research, careers, fashion) to produce a clear, actionable plan.


## Features
- Multi‑agent “team meeting” to analyze a problem and synthesize a consensus plan
- Advisor Category selector with dynamic presets (leader + specialists, goals/roles)
- Category‑specific agenda placeholders, default questions, and guardrails
- Transparent artifacts: full transcript (.md) and raw messages (.json)
- Streamlit UI for agenda, questions, rules, and team configuration
- Clarity Assistant: auto‑suggests clarifying questions; your answers guide the agents
- Optional PubMed search (via the underlying framework)

### Built‑in Categories (editable)
- Medical diagnosis
- Entrepreneur ideas
- NFL fantasy player selection
- Personal finance and investing
- Legal strategy and contracts
- Software architecture and DevOps
- Product design and UX
- Marketing and growth
- Academic research and writing
- Career coaching and hiring
 - Fashion

## Safety & Scope
- Educational/prototype use only; not medical, legal, or financial advice
- Avoid PHI and confidential data; comply with policies and laws
- Human oversight required; verify claims and consult professionals where applicable

## Quickstart
1) Setup
```bash
# Install uv (fast Python package manager)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create and activate venv
uv venv
source .venv/bin/activate

# Install deps
uv pip install -r requirements.txt
```

2) API key
- UI (recommended): create `./.streamlit/secrets.toml`
```toml
OPENAI_API_KEY = "sk-..."
```
- CLI script: create `.env` (used by `medical_consensus.py`)
```bash
cp .env.example .env
# edit .env and set: OPENAI_API_KEY=sk-...
```

3) Run UI
```bash
uv run streamlit run app.py
# open http://localhost:8501
```

## Using Advisors
1) Choose an Advisor Category (top of the main panel)
2) Describe your case/problem in “Case Description (Agenda)”
3) Optionally click “Suggest Questions” and answer clarifiers
4) Review/adjust “Agenda Questions” and “Rules/Guardrails” (auto‑filled per category)
5) Review the prefilled team (leader + specialists) and edit titles/expertise if desired
6) Click “Run Advisors”, then review tabs: Consensus Summary, Transcript, Raw JSON
7) Saved artifacts: `advisor_meetings/<session>.md` and `<session>.json`

## Configuration Tips
- Models: Clarifying questions use your selection (e.g., gpt‑5‑nano). Team meeting uses GPT‑4.1‑nano when a gpt‑5* model is selected (Assistants requirement).
- Fast mode: Toggle on to use 1 round and smaller specialist models for lower latency/cost.
- Web search: DuckDuckGo summaries are on by default. Disable for fully offline runs.
- Caching: Use the “Cache outputs” toggle to reuse recent results; turn off when iterating prompts.
- Actionability: Recommendations are enforced to be short, numbered action plans with owners, deadlines, steps, tools, metrics, risks.
- Safety: Web highlights are rendered safely (no HTML). Secrets should live in `./.streamlit/secrets.toml` only.

## CLI Example
```bash
python medical_consensus.py
```
Edit `AGENDA`, `AGENDA_QUESTIONS`, and `AGENDA_RULES` in the script as needed.

## Deploy
- Local: Streamlit run as above
- Container: build a minimal Python image and expose port 8501
- Internal use: protect behind SSO/reverse proxy; store `.env` securely (not in git)

## License
- App code: MIT (adjust as needed)
- Virtual Lab: see license in the upstream repository
