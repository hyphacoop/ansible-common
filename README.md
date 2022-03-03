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
## common

`common_upgrade`: (true) Upgrade server using `apt upgrade`

`common_basic`: (true) Install additional usefull tools like `curl` and `htop` and `mtr`

`common_build`: (false) Build essetials and git

`common_timezone`: If define sets timezone IE: `America/Toronto`

## firewall

`ipv6_admin_subs:` IPv6 addresses

`ipv4_admin_subs:` IPv4 addresses

## harden_ssh

Locks out root login, and disables password logins on SSH.

## unattended_upgrades

## proxmox_server

Prepeare proxmox server for ansible deploments

## proxmox_provision_vm

Should apply `proxmox_server` to KVM to install promoxer

`add_local_host:` adds host name and ip pair to local /etc/hosts

`pve_kvm_sshkeys:` defines SSH keys to be installed on KVM host

`kvm_start:` Start server and wait for it to start


### Define KVM Nodes Example

```
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

### Sample inventory

```
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
### FAQ

Q: `{"changed": false, "msg": "node 'kvm1' does not exist in cluster"}`

A:  HOSTNAME must match the NODENAME

