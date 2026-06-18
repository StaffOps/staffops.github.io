# Agent Definition

The source of truth for all StaffOps agent behavior.

!!! info "Full documentation"
    The complete documentation lives in the project repository and is available at
    [staffops.github.io/agent-definition/](https://staffops.github.io/agent-definition/).

---

## What it does

Centralizes the definitions, rules, skills, and steering that govern how StaffOps agents behave — across any AI CLI that supports the spec (Claude Code, Kiro).

---

## What's included

| Component | Count | Description |
|---|---|---|
| Agents | 1 + 11 subagents | staffops (coordinator) + domain specialists |
| Skills | 58+ | Lazy-loaded knowledge, on-demand via YAML frontmatter |
| Steering | 21+ global | Universal rules always active (security, git, k8s safety, 12-factor, etc.) |
| Context | Templates + overlays | STAFFOPS.md generic; org-specific overlays (e.g. BDC) |
| Learnings | Structured | troubleshooting, patterns, decisions, infrastructure |

---

## Subagents

`observability` · `documentation` · `anomaly-detection` · `aws` · `finops` · `dev` · `gitops` · `security` · `sre` · `code-review` · `troubleshoot`

---

## Install

```bash
git clone https://github.com/StaffOps/staffops_agent_definition
cd staffops_agent_definition
./setup-agents.sh --install
```

Works with Claude Code and Kiro CLI via symlinks. Org-specific behavior via overlays — no changes to the core repository needed.

---

## Source

[github.com/StaffOps/staffops_agent_definition](https://github.com/StaffOps/staffops_agent_definition)
