# Maturity Score Card

Stateless scoring service for CI/CD maturity metrics.

!!! info "Full documentation"
    The complete documentation lives in the project repository and is available at
    [staffops.github.io/maturity-score-card/](https://staffops.github.io/maturity-score-card/).

---

## What it does

Receives CI/CD tool results (scans, coverage, SLA, incident metrics), computes a 0–100 maturity score per metric, and persists state in PostgreSQL. Scores are exposed on `/metrics`, scraped by VictoriaMetrics, aggregated by `vmalert` recording rules, and visualized in Grafana.

---

## Architecture

```
CI/CD step
    │
    ▼
POST /score              POST /problem/scan-result
    │                           │
    ▼                           ▼
calculate_score()        save problem state
    │                           │
    └──────────┬────────────────┘
               ▼
          PostgreSQL  ◄──── upsert (state persists until next scan)
               │
               ▼
          GET /metrics  ◄──── VictoriaMetrics scrapes every 15s
               │
               ▼
          vmalert  ──── evaluates recording rules ──► VictoriaMetrics
               │
               ▼
            Grafana
```

---

## Scorecards and weights

| Scorecard | Weight | Metrics |
|---|---|---|
| `security` | 35% | `image_scan` (25%), `secret_scan` (25%), `sast` (25%), `dast` (25%) |
| `application` | 25% | `libs_secrets`, `libs_observability`, `unique_db_user`, `health_check`, `unit_coverage`, `integration_coverage`, `stress_test` |
| `reliability` | 40% | `sla` (20%), `change_failure_rate` (30%), `mttr` (25%), `mttd` (25%) |

Weights redistribute automatically among metrics that actually ran — omit a metric to exclude it from the calculation.

---

## Key properties

- Stateless API — all state lives in PostgreSQL
- Weights redistribute automatically for partial pipeline runs
- Slack alerts on new infrastructure problems (`SLACK_BOT_TOKEN`)
- Ships with a full local stack (API, PostgreSQL, VictoriaMetrics, vmalert, Grafana) in `example/`

---

## Quick start

```bash
git clone https://github.com/StaffOps/maturity-score-card
cd maturity-score-card/example
docker compose up --build -d

curl -X POST http://localhost:8080/score \
  -H "Content-Type: application/json" \
  -d '{
    "area": "financial",
    "team": "payments",
    "app": "payments-api",
    "env": "prod",
    "scorecard": "security",
    "metric": "image_scan",
    "raw": {"critical": 0, "high": 1, "medium": 3}
  }'
```

Grafana is available at `http://localhost:3000` (admin / admin).

---

## Source

[github.com/StaffOps/maturity-score-card](https://github.com/StaffOps/maturity-score-card)
