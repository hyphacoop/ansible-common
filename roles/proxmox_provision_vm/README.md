# proxmox_provision_vm

Should apply `proxmox_server` to KVM to install promoxer

- `add_local_host`: adds host name and ip pair to local /etc/hosts
- `pve_kvm_sshkeys`: defines SSH keys to be installed on KVM host
- `kvm_start`: Start server and wait for it to start

TODO: document other vars and dicts in `tasks/main.yml` and defaults.
