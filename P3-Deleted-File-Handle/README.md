# P3 - Deleted File Handle Incident

## Problem

Disk space was not released after deleting a log file.

## Simulation

Created a large file and kept it open with tail.

## Investigation

Used lsof to identify processes holding deleted files.

## Resolution

Killed the process holding the deleted file handle.

## Commands Used

dd
tail
rm
lsof
ps
kill
