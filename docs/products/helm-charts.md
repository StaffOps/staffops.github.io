# Helm Charts

Kubernetes-ready Helm charts for the StaffOps suite.

!!! info "Full documentation"
    The complete documentation lives at
    [staffops.github.io/helm-charts/](https://staffops.github.io/helm-charts/)
    — the same URL also serves the Helm chart index (`index.yaml`).

---

## Available charts

| Chart | Version | Description |
|---|---|---|
| `aigent-squad` | 0.5.0 | Multi-agent platform — supervisor + 5 specialists |
| `staffops-anomaly-detection` | 0.1.0 | Distributed anomaly detection — Go controller + ML |

---

## Add the repository

```bash
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update
```

---

## Install

=== "Aigent Squad"

    ```bash
    helm install aigent-squad staffops/aigent-squad \
      --namespace staffops \
      --create-namespace
    ```

=== "Anomaly Detection"

    ```bash
    helm install anomaly-detection staffops/staffops-anomaly-detection \
      --namespace staffops \
      --create-namespace
    ```

---

## CI/CD

Charts are automatically linted, tested, and published on every merge to `main` via GitHub Actions using `chart-testing` and `chart-releaser-action`.

---

## Source

[github.com/StaffOps/helm-charts](https://github.com/StaffOps/helm-charts)
