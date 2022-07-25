# proxmox_server

Prepare proxmox server for ansible deployments

## Define KVM Nodes Example

```yaml
---
proxmox_server:
  kvm0:
    api_host: '192.168.42.190'
    api_user: 'root@pam'
    api_password: "password"
  kvm1:
    api_host: '192.168.42.196'
    api_user: 'root@pam'
    api_password: "password2"
  kvm2:
    api_host: '192.168.42.196'
    api_user: 'root@pam'
    api_password: "password5"
```

## Sample inventory

```yaml
all:
  vars:
    add_local_host: true
    pve_kvm_sshkeys: "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"
    proxmox_server:
      kvm0:
        api_host: '192.168.42.190'
        api_user: 'root@pam'
        api_password: "password"
  children:
    kvm:
      hosts:
        kvm0:  # Installs necessary items on KVM server
    test1:
      hosts:
        target1: # Deploys server on kvn0
          node: kvm0
          kvm_id: 103
          kvm_template: "Debian10"
          pve_kvm_cores: 4
          pve_kvm_memory: 4000
          pve_disk_size: "10G"
          kvm_ip_address: "192.168.42.62"
          kvm_gw_address: "192.168.42.230"
          kvm_start: true
```
## FAQ

Q: `{"changed": false, "msg": "node 'kvm1' does not exist in cluster"}`

A:  HOSTNAME must match the NODENAME
