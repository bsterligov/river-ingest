# river-ingest

| Crate | Role |
|-------|------|
| `river-sidecar` | OTLP/gRPC receiver (port 4317), in-memory buffer, S3 batch writer |
| `river-ingestion` | S3 poll loop into ClickHouse (logs, traces) and VictoriaMetrics (metrics); applies ClickHouse migrations at startup |

ClickHouse migrations: `river-ingestion/migrations/clickhouse`.

```bash
mise run ci:cargo-test
```

Run the full stack from [river-infra](https://github.com/bsterligov/river-infra). Specs and agent context live in [river-spec](https://github.com/bsterligov/river-spec).
