---
layout: post
author: mjbronarz
title:  "How to resize Nextcloud data disk with ZF"
date:   2020-10-24 21:19:40 +0200
categories: blog zfs linux cloud nextcloud
---
The Nextcloud VM appliance comes configured with two disk - one for the OS and one for data. Both of them are 40g, which is to small to event store one backup of a modern phone. To fix it here is what you need to do:
0. If you have any data on the Nextcloud, make sure you have a backup. 1. Shutdown the host - just in case.2. Login to VMware console and extend the second hard disk to the size you want3. Start the server again4. Login via ssh to nextcloud and become root (sudo su - should do the trick)5. Look at the current zfs configuration: zpool list  and check the disk usage: df -h6. Update the partition size: parted -l than choose the "fix" option when asked7. Delete the "buffer" partition: parted /dev/sdb rm 98. Extend the size of the first partition to utilize 100% of the disk: parted /dev/sdb resizepart 1 100%9. "Unmount" the ZFS pool: zpool export ncdata10. Mount the ZFS pool: zpool import /dev ncdata11. Make the ZFS pool online: zpool online -e ncdata sdb12. Check the new partition size with: zpool list and df -h
