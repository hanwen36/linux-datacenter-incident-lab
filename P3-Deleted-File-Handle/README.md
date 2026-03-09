# P3 - Deleted File Handle Incident Lab

## Overview

This lab simulates a common Linux production issue where disk space is not released even after a file is deleted.

In many real-world systems, a file can be deleted from the filesystem while a running process is still holding the file open. In this situation, the disk space will not be released until the process is terminated.

This lab demonstrates how to identify and resolve this issue.

---

## Scenario

A large log file is created and opened by a running process.  
The file is then deleted while the process still holds the file handle.

Even though the file is deleted, the disk space remains used.

The objective is to identify the process holding the deleted file and release the disk space.

---

## Tools Used

Common Linux troubleshooting tools were used:

- `df`
- `dd`
- `rm`
- `lsof`
- `kill`

---

## Lab Steps

### 1 Create a large test file


dd if=/dev/zero of=big.log bs=1M count=300


This creates a 300MB file.

---

### 2 Simulate a process using the file

A process reads the file so the file descriptor remains open.

---

### 3 Delete the file


rm big.log


The file disappears from the directory but the disk space is still occupied.

---

### 4 Identify deleted files still in use


lsof | grep deleted


This shows processes holding deleted files.

---

### 5 Terminate the process


kill <PID>


After terminating the process, the disk space is released.

---

## Evidence

Screenshots of each step are stored in the `screenshots` folder.

Terminal session logs are stored in:


terminal.log



