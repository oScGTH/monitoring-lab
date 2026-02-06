### Prometheus Installation

On the monitoring server (Fedora), Prometheus was manually installed from
the official binary release. A dedicated service user (`prometheus`) was created,
and Prometheus was configured to run under systemd.

The Prometheus service listens on port 9090 and scrapes configured targets.

## Exporters Setup

### Node Exporter

Node Exporter is installed on all Linux targets. It runs as a dedicated user
and systemd service, exposing metrics on port 9100. It provides metrics for:
- CPU utilization
- Memory usage
- Disk usage
- Network statistics

### Windows Exporter

Windows Exporter runs as a Windows service and exposes metrics on port 9182.
Ensure that the Windows Firewall allows inbound connections on this port. Example
PowerShell firewall rule:

```powershell
New-NetFirewallRule -DisplayName "Allow Windows Exporter" \
  -Direction Inbound -Protocol TCP -LocalPort 9182 -Action Allow ```

Prometheus scrapes both exporters according to its configuration in
/etc/prometheus/prometheus.yml
