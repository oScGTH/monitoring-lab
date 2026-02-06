# Monitoring Lab – Architecture

## Overview
This lab simulates a small operations environment with one dedicated monitoring server
and multiple monitored endpoints across Linux and Windows systems.

## Roles
- Monitoring Server:
  - Fedora Linux
  - Hosts monitoring stack (metrics, alerts, dashboards)

- Monitored Targets:
  - Fedora Linux (self-monitoring)
  - Windows workstation
  - Linux laptop

## Access Model
- SSH-based administration from Linux laptop
- Monitoring server polls or receives metrics from targets

## Network Assumptions
- All systems are on the same local network
- No firewall restrictions between nodes (initial phase)

## Design Goals
- Clear separation between monitoring and monitored systems
- Reproducible setup
- Easy verification of system health and incidents

### Prometheus – Monitoring Engine

- Pull-based metrics collection
- Targets expose a `/metrics` endpoint
- TSDB stores historical data
- PromQL used for querying
- UI available on port 9090
