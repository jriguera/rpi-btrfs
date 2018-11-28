# rpi-btrfs

Scripts to manage RAID btrfs filesystems with systemd

# How it works

Automatically with systemd, when it generates the device/mount units from fstab,
so add an entry in fstab with options like:

```
defaults,noatime,nodiratime,x-systemd.after=/dev/sda,x-systemd.after=/dev/sdb,x-systemd.after=media-volume\x2ddata@dev-sda.service,x-systemd.after=media-volume\x2ddata@dev-sdb.service
```

The unit `media-volume\x2ddata@dev-sda.service` will be automatically called
after the devices are available. The devices `sda` and `sdb` will be part
of a Btrfs raid volume.


More info: https://copyninja.info/blog/systemd_automount_entry.html
