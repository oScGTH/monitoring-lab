# Monitoring Lab

A hands-on monitoring lab designed to document practical experience relevant for an Operations Technician role.

This project demonstrates:
- Installing and configuring a monitoring stack (Prometheus + Alertmanager)
- Collecting metrics from Linux and Windows systems
- Setting up alerting rules for CPU, memory, and disk
- Verifying monitoring and alerting

## Table of Contents

1. [Architecture](#architecture)  
2. [Requirements](#requirements)  
3. [Setup](#setup)  
4. [Exporters](#exporters)  
5. [Alerting](#alerting)  
6. [Alertmanager](#alertmanager)  
7. [Verification](#verification)

## Architecture

The lab consists of:
- **Monitoring Server (Fedora 43)** — runs Prometheus & Alertmanager  
- **Linux Targets (Fedora + Arch)** — expose system metrics via Node Exporter  
- **Windows Target** — exposes metrics via Windows Exporter  
- **Admin Client (Windows/Arch)** — used to administer and verify setup

Metrics flow:
``` Targets → Prometheus → Alertmanager → Receivers (logs, email, webhook) ```

## Requirements

- Fedora 43 monitoring server  
- Linux and Windows endpoints  
- SSH access to Linux systems  
- Windows reachable across network

## Setup

Follow the docs in `docs/` for:
- installing Prometheus and exporters
- configuring scrape targets
- setting up alert rules
- integrating Alertmanager

## Exporters

This lab configures the following exporters:
- **Node Exporter** – for Linux system metrics (CPU, memory, filesystem, network)
- **Windows Exporter** – Windows metrics (services, CPU, memory, disk)

Configured Prometheus scrape targets:
- `prometheus:9090`
- `node_exporter:9100`
- `<windows-ip>:9182`

## Alerting

Basic alert rules are included for:
- High CPU usage (>80%)
- High Memory usage (>80%)
- Low disk space (<15%)

Alerts are configured in:
``` /etc/prometheus/rules/alerts.yml ```


## Alertmanager

Alertmanager is installed on the monitoring server and configured
to receive alerts from Prometheus and route them to receivers.  
By default this lab uses a local log receiver for testing.

## Verification

Use Prometheus UI (`/targets`, `/rules`, `/alerts`) and
Alertmanager UI to verify health and alert delivery.

---

For detailed instructions, see the `docs/` folder.
