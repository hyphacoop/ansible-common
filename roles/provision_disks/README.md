# provision_disks

Partition and mount disks inside the operating system. This will partition the drive, format it as ext4 and mount it to a specific location.

- `provision_disk`: Defines keys to provision
- `key`: Defines the `/dev` device to provision
- `mount_point`: Defines the path the newly provision partition is to be mounted into. 
- `label`: (optional) Defines the label that will be given to the ext4 partition, and used to mount with.

Example: Partition /dev/sdb into /dev/sdb1, and mount it on /mnt/second_drive with label DRIVE2
```yaml
provision_disk: 
"sdb":
    mount_point: /mnt/second_drive
    label: DRIVE2
```