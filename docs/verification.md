## Exporters Verification

### Node Exporter (Linux)

In Prometheus UI → Status → Targets, confirm:
- Target: `localhost:9100`
- State: `UP`

### Windows Exporter

Confirm the Windows Exporter target:
- Target: `<windows-ip>:9182`
- State: `UP`

If status is `DOWN`, verify:
- Exporter service is running on the target system
- Firewall allows inbound traffic on the exporter port
- Prometheus server can reach the IP and port

# Verification

This document outlines how to verify that the monitoring
stack is working correctly.

---

## Prometheus Targets Verification

Visit Prometheus UI → **Status → Targets**

Each target should be listed with state “UP”:

- `prometheus:9090`
- `localhost:9100`
- `<windows-ip>:9182`

If any target is DOWN:
- Verify exporter is running
- Check firewall rules
- Confirm correct IP and port

---

## Rules Verification

Visit Prometheus UI → **Status → Rules**

Confirm alert groups are loaded and enabled:
- HighCPUUsage
- HighMemoryUsage
- LowDiskSpace

---

## Alerts

Visit Prometheus UI → **Alerts**

Alerts should not be firing under normal usage.
To test them, generate load or manually lower thresholds.

---

## Alertmanager Verification

Visit:
``` http://<fedora-ip>:9093 ```

Confirm Alertmanager UI loads and shows any firing alerts.
