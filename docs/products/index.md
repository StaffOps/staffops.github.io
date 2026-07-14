# Products

StaffOps is a suite of open source tools for infrastructure and operations teams.

Each product is independently deployable, but they're designed to work well together.

---

## Aigent Squad

Multi-agent platform for AWS and Kubernetes operations. A supervisor agent routes queries to domain specialists — AWS, Kubernetes, FinOps, DevOps, Observability — and returns consolidated, context-aware responses.

**Read-only by default. Config-driven. Fully observable.**

[Documentation →](aigent-squad.md){ .md-button }

---

## Anomaly Detection

Distributed anomaly detection service for Kubernetes. A Go controller orchestrates parallel workers that query VictoriaMetrics (PromQL) and Loki (LogQL), then correlate signals to fire meaningful alerts through Alertmanager. A Python ML service provides adaptive detection via Isolation Forest and Prophet.

[Documentation →](anomaly-detection.md){ .md-button }

---

## Helm Charts

Kubernetes-ready Helm charts for the full StaffOps suite. Charts available: `aigent-squad`, `anomaly-detection`.

```bash
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update
```

[Documentation →](helm-charts.md){ .md-button }

---

## Maturity Score Card

Stateless FastAPI service that receives CI/CD tool results and computes maturity scores (0–100) per metric — security, application, and reliability scorecards. State persists in PostgreSQL, metrics are scraped by VictoriaMetrics, and results are visualized in Grafana.

[Documentation →](maturity-score-card.md){ .md-button }

---

## OTel Libs

Standardized OpenTelemetry instrumentation libraries for .NET, Python, and Go. OpenTelemetry as the single standard — no vendor SDKs, everything routed through the Collector, with a Prometheus `/metrics` fallback when no OTLP endpoint is configured.

[Documentation →](otel-libs.md){ .md-button }
