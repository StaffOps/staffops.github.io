---
template: home.html
hide:
  - navigation
  - toc
---

# StaffOps

**Open source operations platform for DevOps, SRE and Platform Engineering teams.**

---

## Why StaffOps

Knowledge of infrastructure operations is fragmented, expensive to access, and concentrated in large companies. Smaller teams, independent professionals, and communities don't have access to the same practices, tools, and operational intelligence that enterprises with hundreds of engineers do.

**StaffOps is here to change that.**

We build open source tools that bring AI-assisted operations to everyone — with or without a cloud budget, with or without a dedicated platform team. The goal is a collaborative ecosystem where the community is the real product, not the vendor.

---

## What we build

| Product | Description |
|---|---|
| [**Aigent Squad**](products/aigent-squad.md) | Multi-agent platform for AWS/Kubernetes operations. 1 supervisor + 5 specialist agents, config-driven, read-only by default. |
| [**Anomaly Detection**](products/anomaly-detection.md) | Distributed anomaly detection for Kubernetes. Go controller + workers + Python ML (Isolation Forest, Prophet). |
| [**Helm Charts**](products/helm-charts.md) | Kubernetes-ready Helm charts for the full StaffOps suite. |
| [**Maturity Score Card**](products/maturity-score-card.md) | Stateless scoring service for CI/CD maturity metrics. Computes 0–100 scores per team/app, visualized in Grafana. |
| [**OTel Libs**](products/otel-libs.md) | Standardized OpenTelemetry instrumentation libraries for .NET, Python, and Go — one collector, no vendor SDKs. |

---

## Philosophy

```
Open source. Collaborative. Free.
AI as an amplifier, not a replacement.
```

Everything we build is public — code, architectural decisions, learnings, and operational patterns. Anyone can contribute, adapt, and improve. No dashboards behind a paywall, no vendor lock-in.

AI is one of the means, not the end. The real product is **accessible operational knowledge**, built collectively and versioned like code.

[Read our principles :octicons-arrow-right-24:](community/principles.md){ .md-button }
[How to contribute :octicons-arrow-right-24:](community/contributing.md){ .md-button .md-button--primary }

---

## Quick start

```bash
# Install Helm charts
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update

# Deploy Aigent Squad
helm install aigent-squad staffops/aigent-squad \
  --namespace staffops \
  --create-namespace
```

---

## Community

StaffOps is built in the open. Issues, discussions, and contributions happen on GitHub.

- [GitHub Organization](https://github.com/StaffOps)
- [Open Issues](https://github.com/StaffOps/staffops-aigent-squad/issues)
- [Discussions](https://github.com/StaffOps/staffops-aigent-squad/discussions)
