# Ansible - Hypha


`requirements.yml`
```
---
collections:
- name: https://github.com/hyphacoop/ansible-common.git
  type: git
```
install

```
ansible-galaxy install -r requirements.yml
```
# Roles 

- [common](roles/common/README.md)
- [firewall](roles/firewall/README.md)
- [gather_facts](roles/gather_facts/README.md) - Gathers facts if playbook started skipping facts
- [harden_ssh](roles/harden_ssh/README.md) - Locks out root login, and disables password logins on SSH.
- [nginx](roles/nginx/README.md)
- [node_exporter](roles/node_exporter/README.md) - Install node exporter
- [nodejs](roles/nodejs/README.md) - Install nodejs
- [prometheus](roles/prometheus/README.md) - Install prometheus
- [prometheus_alertmanager](roles/prometheus_alertmanager/README.md)
- [prometheus_exporter_addnode](roles/prometheus_exporter_addnode/README.md)
- [prometheus_exporter_docker](roles/prometheus_exporter_docker/README.md)
- [provision_ssh_keys](roles/provision_ssh_keys/README.md)
- [proxmox_provision_vm](roles/proxmox_provision_vm/README.md) - Provision VM on ProxMox
- [proxmox_server](roles/proxmox_server/README.md) - setups ProxMox server for provisioning
- [ssl](roles/ssl/README.md) - Parent to NGINX, provdes ssl certificates
- [unattended_upgrades](roles/unattended_upgrades/README.md) - Unatteded updates

