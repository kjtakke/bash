# Re-partition Storage

#**Check Current Disk Space**

```bash
df -h
```

**Output:**

```bahs
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        29G  2.5G   2.5G  100% /
devtmpfs        776M     0  776M   0% /dev
tmpfs           937M     0  937M   0% /dev/shm
tmpfs           375M  852K  374M   1% /run
tmpfs           5.0M   12K  5.0M   1% /run/lock
/dev/mmcblk0p1  253M   51M  202M  20% /boot
tmpfs            20M     0   20M   0% /home/pi/redfin/ramfs
tmpfs           188M     0  188M   0% /run/user/1000
```

#**Check Available Disk Space**

```bash
sudo fdisk -l
```

**Look for:**

```bash
Disk /dev/mmcblk0: 29.72 GiB, 31914983424 bytes, 62333952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfbf5b6ae
```

#**Run:**

```bash
sudo apt-get update
sudo apt-get install parted e2fsprogs
sudo parted /dev/mmcblk0
```

**Type:**

```bash
(parted) print
(parted) resizepart 2 100%
(parted) quit
```

#**Run:**

```bash
sudo resize2fs /dev/mmcblk0p2
```

#**Reboot:**

```bahs
sudo reboot
```

#**Check**

```bash
df -h
```

**Output:**

```bahs
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        29G  2.5G   26G   9% /
devtmpfs        776M     0  776M   0% /dev
tmpfs           937M     0  937M   0% /dev/shm
tmpfs           375M  852K  374M   1% /run
tmpfs           5.0M   12K  5.0M   1% /run/lock
/dev/mmcblk0p1  253M   51M  202M  20% /boot
tmpfs            20M     0   20M   0% /home/pi/redfin/ramfs
tmpfs           188M     0  188M   0% /run/user/1000
```