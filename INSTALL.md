Rancher needs more than 10gb

Halt the VM
`vagrant halt`

Clone the VMDK, and convert it to VDI:
`VBoxManage clonehd --format VDI CentOS-Stream-Vagrant-8-20210210.0.x86_64.{vmdk,vdi}`

In the VirtualBOx Virtual Media Manager (File -> Virtual Media Manager) find your new VDI and increase it.
I used 40gb.

In the VM storage settings, attach the new VDI and remove the old VMDK

Boot the VM

Expand the partition:
```
sudo fdisk /dev/sda
d (delete partition)
n (new partition)
p (primary)
1 (default)
2048 (default)
83886079 (default)
n (keep XFS signature)
w (write and exit)
```

Expand the filesystem:
`sudo xfs_growfs /`

Verify:
`df -Th /`
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      xfs    40G   11G   30G  26% /
```

