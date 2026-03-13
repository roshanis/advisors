# Advisors

Advisors is a multi-agent planning app that assembles domain specialists around a problem and produces a clear action plan. Instead of a single model response, it stages a structured discussion across roles such as product, finance, legal, software, marketing, research, career, and fantasy sports.

## What it does

- Runs a team-style multi-agent discussion around a prompt or case
- Uses category presets to preload specialists, goals, and guardrails
- Produces both a readable summary and full meeting artifacts
- Lets you refine the agenda with clarifying questions before the run
- Supports interactive use through a Streamlit interface

## Built-in categories

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

## Safety and scope

- Prototype and educational use only
- Not medical, legal, or financial advice
- Do not enter confidential or regulated data unless you control the environment and policies around it
- Human review is required before acting on the output

## Quick start

### Setup

```bash
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

### API key

For the UI:

```toml
# .streamlit/secrets.toml
OPENAI_API_KEY = "sk-..."
```

For the CLI flow:

```bash
cp .env.example .env
```

Then add `OPENAI_API_KEY` to `.env`.

### Run

```bash
streamlit run app.py
```

Open `http://localhost:8501`.

## Typical workflow

1. Choose an advisor category.
2. Describe the problem or decision to analyze.
3. Use clarifying questions to remove ambiguity.
4. Review the generated team and guardrails.
5. Run the advisor meeting.
6. Read the summary, transcript, and raw JSON artifacts.

Saved outputs land in `advisor_meetings/`.

## Configuration notes

- Clarifying questions use the selected model.
- Fast mode reduces rounds and latency.
- Web search can be disabled for offline or tighter runs.
- Cache controls let you reuse or bypass recent outputs.
- Output formatting is tuned toward short, actionable plans.

## Status

Current status: active prototype for multi-agent decision support across non-medical domains.

## License

MIT for this app code. Upstream framework licensing remains with its original project.
