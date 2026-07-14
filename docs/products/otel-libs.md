# OTel Libs

Standardized OpenTelemetry instrumentation libraries for .NET, Python, and Go.

!!! info "Full documentation"
    The complete documentation lives at
    [staffops.github.io/otel-libs/](https://staffops.github.io/otel-libs/).

---

## What it does

Gives every service the same OpenTelemetry setup regardless of language — one collector endpoint, one set of environment variables, no vendor SDKs.

---

## Libraries

| Language | Package | Status |
|---|---|---|
| .NET | `OtelHelper` (NuGet) | Production |
| Python | `otel-helper` (PyPI) | Production |
| Go | `otelhelper` (Go module) | Production |

Optional AWS, Redis, and SQL instrumentation ship as opt-in extensions per language, so core packages stay lightweight.

---

## Architecture

```
[ Application (.NET / Python / Go) ]
        ↓ OTLP gRPC :4317
[ OpenTelemetry Collector ]
        ↓
┌──────────┬──────────┬──────────┐
│ Traces   │ Metrics  │ Logs     │
│ (Tempo)  │ (VM)     │ (Loki)   │
└──────────┴──────────┴──────────┘
```

---

## Key properties

- OpenTelemetry as the single standard — no vendor SDKs
- Everything exported via the Collector; SDKs never talk to backends directly
- Prometheus `/metrics` fallback (port 9464) when no OTLP endpoint is configured
- Sampling and resource attributes applied at the Collector, not the SDK
- TLS by default for OTLP endpoints; opt out explicitly for local plaintext collectors

---

## Quick start

=== "\.NET"

    ```csharp
    services.AddOtelHelper();
    ```

=== "Python"

    ```python
    from otel_helper import setup_telemetry
    setup_telemetry()
    ```

=== "Go"

    ```go
    import otelhelper "github.com/staffops/staffops-otel-libs/go"

    shutdown, err := otelhelper.Setup(ctx)
    defer shutdown(ctx)
    ```

---

## Source

[github.com/StaffOps/otel-libs](https://github.com/StaffOps/otel-libs)
