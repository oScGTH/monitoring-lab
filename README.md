# Monitoring Lab

A hands-on monitoring lab.

The lab focuses on:
- Linux system monitoring
- Service availability and health checks
- Alerting and basic incident verification
- Operational documentation and verification

This repository will evolve step by step and includes architecture notes, setup instructions, and verification examples.

## How it Works – Overview

This project uses Prometheus as the core monitoring system. Prometheus works by scraping metrics endpoints exposed by systems or exporters over HTTP. It stores the data in a time-series database and allows querying using PromQL.

The first scrape job configured is Prometheus itself, accessible at `http://<fedora-ip>:9090`.

### Exporters and Scrape Targets

This lab uses exporters to expose system metrics for Prometheus to scrape:

- **Node Exporter** – Installed on Linux systems to expose system and hardware metrics (CPU, memory, filesystem, network, etc.) on port 9100.
- **Windows Exporter** – Installed on Windows to expose performance metrics on port 9182.

Configured Prometheus scrape targets:
- `prometheus:9090` — Prometheus itself
- `localhost:9100` — Node Exporter (Fedora)
- `<windows-ip>:9182` — Windows Exporter
