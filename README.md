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
