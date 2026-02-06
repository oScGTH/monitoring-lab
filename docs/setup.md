### Prometheus Installation

On the monitoring server (Fedora), Prometheus was manually installed from
the official binary release. A dedicated service user (`prometheus`) was created,
and Prometheus was configured to run under systemd.

The Prometheus service listens on port 9090 and scrapes configured targets.
