# Setup Documentation

This document outlines how the monitoring stack is installed
and configured on the monitoring server and targets.

---

## Prometheus Installation

Prometheus is installed manually on the Fedora monitoring server.
A dedicated user runs the Prometheus service, and the binary is
placed in `/usr/local/bin`.

The main configuration file is:
``` /etc/prometheus/prometheus.yml ```

---

## Exporters and Prometheus Scraping

Prometheus collects metrics from targets by scraping
HTTP endpoints exposed by exporters.

Example `scrape_configs` from `prometheus.yml`:

```yaml
global:
  scrape_interval: 15s

rule_files:
  - "rules/alerts.yml"

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]

  - job_name: "node_exporter"
    static_configs:
      - targets: ["localhost:9100"]

  - job_name: "windows_exporter"
    static_configs:
      - targets: ["<windows-ip>:9182"]
```

## Firewall configuration (Windows)

Windows Firewall must allow inbound TCP 9182:

```
New-NetFirewallRule -DisplayName "Allow Windows Exporter" `
  -Direction Inbound -Protocol TCP -LocalPort 9182 -Action Allow
```

## Alert Rules
Alert rules are defined in:

``` /etc/prometheus/rules/alerts.yml ```

They are loaded by Prometheus using the rule_files: directive.

The rules include thresholds for CPU, memory, and disk usage.

## Alertmanager Setup

Alertmanager is installed on the monitoring server:

Binary located at /usr/local/bin/alertmanager

Config file at /etc/alertmanager/alertmanager.yml

Runs as a systemd service

Alertmanager listens on port 9093 by default and receives
alerts from Prometheus.


---
