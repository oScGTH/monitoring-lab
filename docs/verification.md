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
