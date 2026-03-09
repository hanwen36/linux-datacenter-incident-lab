# P5 - Log Explosion Incident

## Overview

This project simulates a Linux system where a log file grows rapidly and consumes large amounts of disk space.

The objective is to reproduce the issue, identify the large log file, and restore normal system disk usage.

The lab environment uses Ubuntu Linux running in VirtualBox.

---

## Problem

A log file grew uncontrollably and consumed a large amount of disk space.

Log explosions commonly occur when an application repeatedly writes error messages to a log file.

---

## Simulation

A log file was created and continuously written using the `yes` command.

Example command used:

yes "ERROR application failure detected" >> app.log

The log file grew rapidly and consumed disk space.

Disk usage was inspected using:

du -sh *

Example output:

61G app.log

---

## Investigation

The large log file was identified using:

du -sh *

This confirmed that the log file was responsible for consuming disk space.

---

## Resolution

The log file was cleared using:

truncate -s 0 app.log

After truncating the log file, disk usage returned to normal.

---

## Commands Used

| Command | Purpose |
|-------|-------|
| yes | Generate continuous log entries |
| du | Check file sizes |
| truncate | Clear the log file |
| df | Verify disk usage |
