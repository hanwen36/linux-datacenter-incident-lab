P3 - Deleted File Handle Incident
Overview

This project simulates a common Linux storage issue where disk space is not released after a file is deleted.
The problem occurs when a running process still holds an open file handle to the deleted file.

This scenario frequently appears in production environments when large log files are deleted while still being used by an active process.

Problem

Disk space remained occupied even after a large log file was deleted.

Although the file no longer appeared in the directory listing, the space was not returned to the filesystem.

Simulation

The issue was reproduced by:

Creating a large log file

Opening the file with a running process (tail)

Deleting the file while the process still had the file open

Because the process continued to hold the file descriptor, the disk space remained allocated.

Investigation

The investigation focused on identifying processes that were still holding deleted files.

The lsof command was used to locate open file handles marked as deleted.

Example investigation command:

lsof | grep deleted

This revealed the process that continued to hold the file descriptor.

Resolution

The issue was resolved by terminating the process that held the deleted file handle.

Once the process stopped, the filesystem released the disk space.

Verification was performed using:

df -h

Disk space returned to normal after the process was terminated.

Commands Used
Command	Purpose
dd	Create a large test file
tail	Keep the file open with a running process
rm	Delete the file while still open
lsof	Identify processes holding deleted files
ps	Inspect running processes
kill	Terminate the process holding the file
Skills Demonstrated

Linux filesystem troubleshooting

File descriptor investigation

Production-style incident analysis

Process management

Root cause analysis
