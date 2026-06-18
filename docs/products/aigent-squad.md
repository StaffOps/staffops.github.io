# AIgent Squad

AIgent Squad is a multi-agent AI platform for AWS and Kubernetes operations. It
receives natural-language operational questions, classifies them with a lightweight
Bedrock call, and routes them to the right specialist agent — each of which
collects read-only context from its data sources and synthesizes a structured
answer using Claude on AWS Bedrock.

---

## Specialist agents

| Agent | Domain |
|-------|--------|
| **Supervisor** | Query classification, routing, and fan-out orchestration |
| **AWS** | EC2, EKS, IAM, S3, RDS, VPC, Cost Explorer |
| **Kubernetes** | Pods, deployments, services, events, metrics |
| **FinOps** | Cost analysis, savings plans, budget attribution |
| **DevOps** | CI/CD pipelines, GitLab, Jira, deployment tracking |
| **Observability** | Prometheus metrics, logs, traces, alert triage |

---

## Key properties

| Property | Detail |
|----------|--------|
| **Read-only by default** | Agents never execute mutations — analysis and recommendations only |
| **Config-driven** | Add an agent with two files (`agent.yaml` + `prompt.md`), no code changes |
| **Single image** | All agents run in-process in one container for simple deployments |
| **Cost attributed** | Per-agent token counting and estimated USD cost via Bedrock inference profiles |
| **Observable** | OTel traces, RED metrics, and structured JSON logs on every component |
| **Conversation history** | DynamoDB with 24 h TTL per user and session |

---

## Quick install

```bash
helm repo add staffops https://staffops.github.io/helm-charts/
helm repo update

helm install aigent-squad staffops/aigent-squad \
  --namespace aigent-squad --create-namespace \
  --set redis.host=<your-elasticache-endpoint>
```

**Docker Hub**: `karlipegomes/aigent-squad:latest` (multi-arch `amd64` + `arm64`)

!!! info "Distributed topology available"
    The Helm chart supports a `distributed` topology where each agent runs as its
    own Deployment with an independent ServiceAccount and IRSA role. Pass
    `--set topology=distributed` or use the provided `values-distributed.yaml`.

---

## Links

- [Full documentation](https://staffops.github.io/staffops-aigent-squad/) — architecture, setup, agent reference, runbooks
- [Source code](https://github.com/StaffOps/staffops-aigent-squad) — Apache 2.0

---

## License

Apache 2.0 — see [LICENSE](https://github.com/StaffOps/staffops-aigent-squad/blob/main/LICENSE).
