# Anomaly Detection

Distributed anomaly detection service for Kubernetes clusters.

!!! info "Full documentation"
    The complete documentation lives in the project repository and is available at
    [staffops.github.io/anomaly-detection/](https://staffops.github.io/anomaly-detection/).

---

## What it does

Queries VictoriaMetrics and Loki continuously, detects statistical and ML-based anomalies, correlates signals across sources, and fires actionable alerts through Alertmanager.

---

## Architecture

```
Controller (Go, HA)
     ↓ gRPC
Workers (Go, stateless) ──→ VictoriaMetrics (PromQL)
     ↓                   ──→ Loki (LogQL)
ML Service (Python)
     ↓
Alertmanager
```

| Component | Technology | Replicas | Role |
|---|---|---|---|
| Controller | Go + gRPC | 2 (HA Lease) | Orchestrates detection cycles, correlates anomalies |
| Workers | Go + gRPC | 3 (stateless) | Executes queries, runs detection algorithms |
| ML Service | Python + FastAPI | 1 | Isolation Forest + Prophet forecasting |
| Redis | KV store | 1 | Baselines, dedup TTL, seasonal profiles |

---

## Detection algorithms

- **Z-Score (adaptive)** — statistical threshold with seasonal adjustment
- **EWMA** — exponentially weighted moving average
- **Isolation Forest** — multivariate ML-based outlier detection
- **Prophet** — time-series forecasting for expected vs actual comparison

---

## Quick install

```bash
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update

helm install anomaly-detection staffops/staffops-anomaly-detection \
  --namespace staffops \
  --create-namespace \
  --set victoriaMetrics.url=http://vmselect:8481/select/0/prometheus
```

---

## Source

[github.com/StaffOps/staffops-anomaly-detection](https://github.com/StaffOps/staffops-anomaly-detection)
