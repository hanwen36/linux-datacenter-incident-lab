# P1 - Disk Full Incident

## Overview

This project simulates a common Linux infrastructure incident where a system runs out of disk space.

The goal of this lab is to:

- simulate disk exhaustion
- investigate which files consume disk space
- restore the system to a healthy state

Environment:

Ubuntu Linux running in VirtualBox.

---

## Incident Summary

Incident Type: Disk Space Exhaustion  
Environment: Ubuntu Linux VM  
Impact: System cannot write new data

Observed error:


No space left on device


This type of incident commonly occurs when:

- log files grow uncontrollably
- temporary files accumulate
- monitoring or cleanup processes fail

---

## Simulation

Initial disk usage:


df -h


Example output:


/dev/sda2 30G 6.9G 22G 25% /


Large files were created to simulate heavy disk usage:


fallocate -l 18G bigfile1
fallocate -l 2G bigfile2


Disk usage increased:


/dev/sda2 30G 27G 1.1G 97% /


Disk was filled completely using:


dd if=/dev/zero of=triggerfile bs=100M status=progress


System returned:


No space left on device


---

## Investigation

Identify large files consuming disk space:


du -ah . | sort -rh | head


Example result:


19G ./bigfile1
2.1G ./bigfile2
1.1G ./triggerfile


---

## Resolution

Remove large files:


rm bigfile1 bigfile2 triggerfile


Verify disk recovery:


df -h


Disk usage returned to normal.

---

## Evidence

Terminal session log:

terminal.log

Screenshots:

screenshots/
