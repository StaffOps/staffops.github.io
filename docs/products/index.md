# Products

StaffOps is a suite of open source tools for infrastructure and operations teams.

Each product is independently deployable, but they're designed to work well together.

---

## Aigent Squad

Multi-agent platform for AWS and Kubernetes operations. A supervisor agent routes queries to domain specialists — AWS, Kubernetes, FinOps, DevOps, Observability — and returns consolidated, context-aware responses.

**Read-only by default. Config-driven. Fully observable.**

[Documentation →](aigent-squad.md){ .md-button }

---

## ChaiTops

Conversational orchestrator for observability stacks. Provides a chat interface (LibreChat) backed by a FastAPI orchestrator that integrates with multiple AI CLI adapters. Designed for querying and diagnosing OpenTelemetry, VictoriaMetrics, Tempo, and Loki pipelines.

[Documentation →](chaitops.md){ .md-button }

---

## Anomaly Detection

Distributed anomaly detection service for Kubernetes. A Go controller orchestrates parallel workers that query VictoriaMetrics (PromQL) and Loki (LogQL), then correlate signals to fire meaningful alerts through Alertmanager. A Python ML service provides adaptive detection via Isolation Forest and Prophet.

[Documentation →](anomaly-detection.md){ .md-button }

---

## Agent Definition

The source of truth for all StaffOps agent behavior. Defines the core agent, 11 specialist subagents, 58+ lazy-loaded skills, and 21+ global steering rules. Template-driven, version-controlled, and installable via symlinks in Claude Code or Kiro CLI.

[Documentation →](agent-definition.md){ .md-button }

---

## Helm Charts

Kubernetes-ready Helm charts for the full StaffOps suite. Charts available: `aigent-squad`, `anomaly-detection`.

```bash
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update
```

[Documentation →](helm-charts.md){ .md-button }
