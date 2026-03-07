# Runbook – Disk Full Incident

This runbook describes the basic steps used to investigate and resolve a disk full condition on a Linux system.

Step 1 – Check current disk usage

Run the following command to check filesystem usage:

df -h

If the disk usage is close to 100%, the system may experience storage issues such as "No space left on device".

Step 2 – Identify large files

To find which files or directories are consuming the most disk space, run:

du -ah . | sort -rh | head

This command lists the largest files in the current directory.

Step 3 – Locate the cause

In this lab environment, large files were intentionally created to simulate disk usage:

bigfile1  
bigfile2  
triggerfile

These files occupy most of the disk space.

Step 4 – Remove unnecessary files

Delete the large files to free disk space:

rm bigfile1 bigfile2 triggerfile

Step 5 – Verify disk recovery

Run the command again to confirm that disk space has been restored:

df -h

If disk usage returns to normal levels, the issue has been resolved.
