# ChaiTops

Conversational orchestrator for observability stacks.

!!! info "Full documentation"
    The complete ChaiTops documentation lives in the project repository and is available at
    [staffops.github.io/chaitops/](https://staffops.github.io/chaitops/).

---

## What it does

ChaiTops provides a chat interface to query and diagnose observability pipelines — OpenTelemetry, VictoriaMetrics, Tempo, Loki, and Grafana — without needing to know PromQL, LogQL, or the underlying tooling.

---

## Architecture

```
LibreChat (UI) ──→ Agent API (FastAPI) ──→ Agent Adapters
                                              ├─ Claude API
                                              ├─ Kiro CLI
                                              └─ OpenCode
```

- **LibreChat** — conversational frontend with authentication and history
- **Agent API** — FastAPI orchestrator with workspace isolation per session
- **Adapters** — pluggable CLI backends, CLI-agnostic by design
- **MCP Manager** — Model Context Protocol server integration
- **Redis** — session state, job queue, agent locks
- **DynamoDB** — conversation history with 24h TTL

---

## Key properties

- Multi-CLI adapter support (Claude, Kiro, OpenCode)
- Streaming responses for long-running tasks
- Workspace isolation per session
- Future-ready for Slack/Teams/Discord integration

---

## Quick start

```bash
git clone https://github.com/StaffOps/staffops-chaitops
cd staffops-chaitops
cp .env.example .env
# fill in your credentials
docker compose up -d
```

---

## Source

[github.com/StaffOps/staffops-chaitops](https://github.com/StaffOps/staffops-chaitops)
