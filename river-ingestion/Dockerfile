FROM rust:1.95-slim-trixie AS builder
WORKDIR /app
COPY Cargo.toml Cargo.lock ./
COPY river-sidecar ./river-sidecar
COPY river-ingestion ./river-ingestion
RUN cargo build --release --package river-ingestion

FROM debian:trixie-slim
RUN apt-get update && apt-get install -y ca-certificates && rm -rf /var/lib/apt/lists/*
COPY --from=builder /app/target/release/river-ingestion /usr/local/bin/river-ingestion
CMD ["river-ingestion"]
