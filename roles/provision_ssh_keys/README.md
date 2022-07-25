# provision_ssh_keys

Adds sysadmin user, sets root and sysadmin passwords, adds SSH keys to sysadmin.

- `root_password`: (undefined) set root password (SHA-512 password hash)
- `sysadmin_password`: (undefined) set sysadmin password (SHA-512 password hash)
- `ssh_user_keys`: (undefined) dict of user SSH keys
    - `name`: cosmetic name of user
    - `key`: Key to be added
- `ssh_additional_user_keys`: (undefined) additional keys that will be added to `ssh_user_keys`



Example: adds user1 and user2 keys to sysadmin on all hosts, also adds user3 to computer2.com
```yaml
all:
  vars:
    ssh_user_keys:
        - name: user1
        key: "ssh-rsa ABCDEF user1@computer1"
        - name: user2
    key: "ssh-ed25519 ABCDEFG user2@computer2"
    #...#
hosts:
    computer1.com
    computer2.com
    ssh_additional_user_keys:
      - name: user3
        key: "ssh-rsa user3 user3@computer3"
```