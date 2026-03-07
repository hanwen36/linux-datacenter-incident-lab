# Disk Full Incident Response Lab

This project demonstrates how to simulate and troubleshoot a disk full condition on a Linux system.

The lab environment uses Ubuntu running in VirtualBox. The goal of the exercise is to intentionally fill the disk space, observe the system behavior when storage becomes exhausted, and then apply standard Linux troubleshooting commands to identify and resolve the issue.

The process begins by checking the current disk usage using the following command:

df -h

Large files are then created to simulate heavy disk usage:

fallocate -l 18G bigfile1
fallocate -l 2G bigfile2

Disk usage is checked again to confirm that the system is approaching full capacity.

Next, additional data is written to trigger the disk full condition:

dd if=/dev/zero of=triggerfile bs=100M status=progress

At this point the system produces the expected error:

No space left on device

To identify which files are consuming the most storage, the following command is used:

du -ah . | sort -rh | head

This command lists the largest files in the directory and helps quickly locate the source of disk usage.

After identifying the large files, they are removed:

rm bigfile1 bigfile2 triggerfile

Finally, disk usage is checked again:

df -h

After deleting the unnecessary files, the disk space returns to normal and the system functions correctly again.

This lab demonstrates a typical troubleshooting workflow used by Linux administrators and data center technicians when responding to disk space incidents.
