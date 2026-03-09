# P6 - RAID Degraded Incident

## Overview

This project simulates a degraded RAID array in a Linux environment.

The objective is to reproduce a RAID degraded state, investigate the issue, and restore the array to a healthy state.

The lab environment uses Ubuntu Linux running in VirtualBox.

---

## Problem

A RAID array entered a degraded state after one of the disks failed.

In a degraded RAID state, the system continues to operate but redundancy is lost.

---

## Simulation

A RAID1 array was created using two loop devices.

Example command used:

mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/loop0 /dev/loop1

The RAID status was verified using:

cat /proc/mdstat

---

## Investigation

A disk failure was simulated using:

mdadm /dev/md0 --fail /dev/loop1

The disk was then removed:

mdadm /dev/md0 --remove /dev/loop1

The RAID status showed a degraded state:

[2/1] [_U]

---

## Resolution

A replacement disk was added back to the array:

mdadm /dev/md0 --add /dev/loop1

After rebuilding, the RAID returned to a healthy state:

[UU]

---

## Commands Used

| Command | Purpose |
|--------|--------|
| mdadm | Manage RAID arrays |
| losetup | Create loop devices |
| dd | Create disk images |
| cat | Check RAID status |
