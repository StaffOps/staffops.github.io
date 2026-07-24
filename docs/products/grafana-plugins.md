# Grafana Plugins

Monorepo of Grafana plugins (panels and apps) for the StaffOps platform.

!!! info "Full documentation"
    The complete documentation lives at
    [staffops.github.io/grafana-plugins/](https://staffops.github.io/grafana-plugins/).

---

## Plugins

| Plugin | Type | What it does |
|--------|------|--------------|
| **Service Map Panel** | `panel` | DAG service map from Tempo service-graph metrics — health coloring, animated traffic, cascade filtering, drill-down. |
| **AIgent Squad Chat** | `app` | Conversational UI to AIgent Squad (SRE-agentic assistant) — streams answers through the Grafana LLM app. |

---

## Design principles

| Principle | Detail |
|-----------|--------|
| **Frontend-only** | No Go backends; secrets and orchestration live in existing services (LLM app, datasources). |
| **One package per plugin** | Independent versioning, signing, and release per plugin. |
| **Docker-only builds** | No local SDKs required — Node 22 + pnpm run inside containers. |
| **Spec-driven** | Each feature has `specs/<feature>/{requirements,design,tasks}.md` before code. |

---

## Quick start

```bash
cd packages/staffops-servicemap-panel

# Build the plugin
docker run --rm -v "$(pwd)/../..:/w" -w /w/packages/staffops-servicemap-panel node:22 npm run build

# Start Grafana with the plugin loaded
docker compose up -d
```

Each plugin ships its own `docker-compose.yaml` + provisioning + `.env.example`.

---

## Source

[github.com/StaffOps/grafana-plugins](https://github.com/StaffOps/grafana-plugins) — MIT
