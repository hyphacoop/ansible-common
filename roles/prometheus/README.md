# Prometheus

Installs Prometheus stack
- Prometheus
- Grafana
- Prometheus-pve

`prometheus_version`: (2.34.0-rc.0) Version to download
`grafana_install`: (true) Install Grafana
`prometheus_pve_install`: (true) Install prometheus PVE exporter proxy

Setup outbound email for grafana by defining the following fields:
- `outbound_email_hostname`
- `outbound_email_port`
- `outbound_email_login`
- `outbound_email_password`
- `outbound_email_address`

`pve_root_password`: Define for root access to PVE
