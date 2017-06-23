# lvm-extend

### Rescan devices
    echo '1' > /sys/class/scsi_disk/0\:0\:0\:0/device/rescan
### Open fdisk
    fdisk /dev/sda
### Delete partition
```
Command (m for help): d
Partition number (1-X): X
```
### Recreate partition (p)
```
Command (m for help): n
Command action
e extended
p primary partition (1-X)
p
Selected partition X
```
### Change type (LVM = 8e)
```
Command (m for help): t
Partition number (1-4): 4
Hex code (type L to list codes): 8e
```
### Write changes 

    Command (m for help): w

### Sync disks
    # partprobe -s

### Reprobe partition table
    # pvresize /dev/sda4

### Extend Logical Volume
    # lvextend -L+XG /dev/vg/vol-name

### Extend fs in logical volume
    # resize2fs /dev/vg/vol-name
