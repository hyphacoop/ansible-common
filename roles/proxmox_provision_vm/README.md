# proxmox_provision_vm

Should apply` proxmox_server` to KVM to install promoxer

-` proxmox_server`: Dict of proxmox servers and credentials
    -` key`: Hostname of proxmox server
        -` api_host`: address of server
        -` api_user`: username to login as
        -` api_password`: password to login as

-` add_local_host`: adds host name and ip pair to local /etc/hosts
-` pve_kvm_sshkeys`: defines SSH keys to be installed on KVM host
-` node`: hostname listed in proxmox_server
-` kvm_start`: Start server and wait for it to start
-` kvm_id`: Assigns ID in proxmox 206
-` kvm_net_0:` Defines first interface using proxmox format (IE "virtio=00:50:00:5a:55:55,bridge=vmbr0")
-` kvm_ip_address`: Defines ipv4 address in cloud-init
-` kvm_gw_address`: Defines ipv4 gateway in cloud-init
-` kvm_ip_address_cidr`: Defines ipv4 CIDR
-` kvm_gw6_address`: Defines ipv6 address in cloud-init
-` kvm_ip6_gateway`: Defines ipv6 gateway in cloud-init
-` kvm_ip6_address_cidr`: Defines ipv6 CIDR
-` kvm_net_1:` Defines first interface using proxmox format (IE "virtio,bridge=vmbr1")
-` kvm1_ip_address`: Defines ipv4 address on second interface in cloud-init
-` kvm1_ip6_address`: Defines ipv6 address on second interface in cloud-init

Following are mappings to the ansible proxmox plugin. See  [community.general.proxmox](https://docs.ansible.com/ansible/latest/collections/community/general/proxmox_module.html) for more details.

` pve_kvm_update` : ('yes') update
` node` :  node
` proxmox_api_user` :  api_user
` proxmox_api_password` :  api_password
` proxmox_api_host` :  api_host
` kvm_id` :  vmid
` pve_kvm_proxmox_default_behavior` : ('compatibility')
` pve_kvm_validate_certs` : (undefined) validate_certs
` pve_hostname` : (undefined) name
` pve_kvm_timeout` : (undefined) timeout
` pve_kvm_description` : (undefined) description
` pve_kvm_hardware_virtualization` : (undefined) kvm
` pve_kvm_ostype` : (undefined) ostype
` pve_kvm_sockets` : (undefined) sockets
` pve_kvm_cores` : (undefined) cores
` pve_kvm_cpu` : (undefined) cpu
` pve_kvm_cpuunits` : (undefined) cpuunits
` pve_kvm_cpulimit` : (undefined) cpulimit
` pve_kvm_memory` : (undefined) memory
` pve_kvm_balloon` : (undefined) balloon
` pve_kvm_vga` : (undefined) vga
` pve_kvm_acpi` : (undefined) acpi
` pve_kvm_agent` : (undefined) agent
` pve_kvm_args` : (undefined) args
` pve_kvm_autostart` : (undefined) autostart
` pve_kvm_bios` : (undefined) bios
` pve_kvm_boot` : (undefined) boot
` pve_kvm_bootdisk` : (undefined) bootdisk
` pve_kvm_citype` : (undefined) citype
` pve_kvm_cicustom` : (undefined) cicustom
` pve_kvm_ciuser` : (undefined) ciuser
` pve_kvm_cipassword` : (undefined) cipassword
` pve_kvm_sshkeys` : (undefined) sshkeys
` pve_kvm_ipconfig` : (undefined) ipconfig
` pve_kvm_nameservers` : (undefined) nameservers
` pve_kvm_searchdomains` : (undefined) searchdomains
` pve_kvm_delete` : (undefined) delete
` pve_kvm_digest` : (undefined) digest
` pve_kvm_force` : (undefined) force
` pve_kvm_freeze` : (undefined) freeze
` pve_kvm_hostpci` : (undefined) hostpci
` pve_kvm_hotplug` : (undefined) hotplug
` pve_kvm_hugepages` : (undefined) hugepages
` pve_kvm_keyboard` : (undefined) keyboard
` pve_kvm_localtime` : (undefined) localtime
` pve_kvm_lock` : (undefined) lock
` pve_kvm_machine` : (undefined) machine
` pve_kvm_migrate_downtime` : (undefined) migrate_downtime
` pve_kvm_migrate_speed` : (undefined) migrate_speed
` pve_kvm_numa` : (undefined) numa
` pve_kvm_numa_enabled` : (undefined) numa_enabled
` pve_onboot` : (undefined) onboot
` pve_kvm_parallel` : (undefined) parallel
` pve_kvm_pool` : (undefined) pool
` pve_kvm_protection` : (undefined) protection
` pve_kvm_reboot` : (undefined) reboot
` pve_kvm_revert` : (undefined) revert
` pve_kvm_scsihw` : (undefined) scsihw
` pve_kvm_serial` : (undefined) serial
` pve_kvm_shares` : (undefined) shares
` pve_kvm_skiplock` : (undefined) skiplock
` pve_kvm_smbios` : (undefined) smbios
` pve_kvm_startdate` : (undefined) startdate
` pve_kvm_startup` : (undefined) startup
` pve_kvm_state` : (undefined) state
` pve_kvm_tablet` : (undefined) tablet
` pve_kvm_tags` : (undefined) tags
` pve_kvm_tdf` : (undefined) tdf
` pve_kvm_vcpus` : (undefined) vcpus
` pve_kvm_watchdog` : (undefined) watchdog
