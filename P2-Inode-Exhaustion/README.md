# P2 – Inode Exhaustion Incident Lab

## Overview

This lab simulates a common Linux production incident where the system reports:

"No space left on device"

even though disk space is still available.

The root cause is **inode exhaustion** caused by a large number of small files.

This scenario is common in environments such as:

- Data centers
- Logging systems
- Temporary file directories
- Containerized workloads

---

## Incident Scenario

A system begins failing to create new files with the error:

