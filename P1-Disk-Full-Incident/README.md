# P1 – Disk Full Incident Response Lab

## Part 1 – Incident Simulation

This project demonstrates how to simulate a disk full condition on a Linux system and perform standard troubleshooting steps to resolve the issue.

The lab environment uses Ubuntu running in VirtualBox. The objective is to intentionally fill disk space and observe how the system behaves when storage becomes exhausted.

First, check the current disk usage:

df -h

Large files are created to simulate heavy disk usage:

fallocate -l 18G bigfile1
fallocate -l 2G bigfile2

Disk usage is checked again:

df -h

Next, additional data is written to trigger the disk full condition:

dd if=/dev/zero of=triggerfile bs=100M status=progress

The system then produces the expected error:

No space left on device

---

## Part 2 – Investigation and Resolution

To identify which files are consuming the most disk space, run:

du -ah . | sort -rh | head

Example output:

19G ./bigfile1  
2.1G ./bigfile2  
1.1G ./triggerfile  

These files consumed most of the available disk capacity.

The large files are removed to restore disk space:

rm bigfile1 bigfile2 triggerfile

Finally, verify that disk space has recovered:

df -h

After removing the unnecessary files, disk usage returns to normal and the system functions correctly again.

---

## Evidence

Terminal session logs are included in:

terminal.log

Screenshots are included in:

screenshots/
