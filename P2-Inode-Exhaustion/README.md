# P2 - Inode Full Incident

## Overview

This lab simulates a Linux filesystem issue where all available inodes are consumed.

Even when disk space is still available, the system cannot create new files because no free inodes remain.

Environment:

Ubuntu Linux VM running in VirtualBox.

---

## Problem

The system returned the following error when attempting to create files:


No space left on device


However, disk space was still available.  
The root cause was that all filesystem inodes were consumed.

---

## Simulation

Create a small filesystem image with a limited number of inodes:


dd if=/dev/zero of=inodelab.img bs=1M count=16
mkfs.ext4 -N 128 inodelab.img


Mount the filesystem:


mkdir mnt
sudo mount -o loop inodelab.img mnt


Check inode usage:


df -i mnt


---

## Investigation

Create many small files until the inode limit is reached:


touch file1
touch file2
...


Eventually the system returns:


No space left on device


Check inode usage again:


df -i


Example result:


/dev/loop0 128 128 0 100%


This confirms all inodes are consumed.

---

## Resolution

Remove unnecessary files:


rm -rf smallfiles


Verify inode recovery:


df -i


Inodes should now be available again.

