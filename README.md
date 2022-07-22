# Ansible - Hypha


## Add to your Ansible repo

Add to `requirements.yml`:
```yaml
---
collections:
- name: https://github.com/hyphacoop/ansible-common.git
  type: git
```

Install with:

```
ansible-galaxy install -r requirements.yml
```

## Using

Our `setup` role conflicts with Ansible's built-in one. In general modules should be specified by their full path, like `hypha.common.setup` and `ansible.builtin.setup`.

# Roles 

- [setup](roles/setup/README.md) - setup server for use
- [firewall](roles/firewall/README.md) - setup system and docker firewall
- [gather_facts](roles/gather_facts/README.md) - gathers facts if playbook started skipping facts
- [harden_ssh](roles/harden_ssh/README.md) - locks out root login, and disables password logins on SSH
- [loki](roles/loki/README.md) - install loki
- [nginx](roles/nginx/README.md) - install nginx and set up reverse-proxies
- [node_exporter](roles/node_exporter/README.md) - install node_exporter
- [nodejs](roles/nodejs/README.md) - install nodejs
- [prometheus](roles/prometheus/README.md) - install prometheus
- [prometheus_alertmanager](roles/prometheus_alertmanager/README.md) - installs alertmanager
- [prometheus_alertmanager_matrix](roles/prometheus_alertmanager_matrix/README.md) - installs a matrix bot for alertmanager
- [prometheus_exporter_addnode](roles/prometheus_exporter_addnode/README.md) - add node config to prometheus
- [prometheus_exporter_docker](roles/prometheus_exporter_docker/README.md) - installs cAdvisor
- [promtail](roles/promtail/README.md) - installs promtail for loki
- [provision_disks](roles/provision_disks/README.md) - partition and mount disks
- [provision_ssh_keys](roles/provision_ssh_keys/README.md) - setup sysadmin user, set passwords, add SSH keys
- [proxmox_provision_vm](roles/proxmox_provision_vm/README.md) - provision VM on ProxMox
- [proxmox_server](roles/proxmox_server/README.md) - setup ProxMox server for provisioning
- [ssl](roles/ssl/README.md) - parent to nginx, provdes ssl certificates
- [unattended_upgrades](roles/unattended_upgrades/README.md) - setup unattended upgrades