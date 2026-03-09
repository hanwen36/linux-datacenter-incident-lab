P4 README.md
# P4 - High IO Incident

## Overview

This project simulates a Linux system experiencing high disk I/O usage.

The objective is to reproduce the issue, investigate the process causing the high I/O load, and restore normal system performance.

The lab environment uses Ubuntu Linux running in VirtualBox.

---

## Problem

The system experienced very high disk I/O utilization.

High disk I/O can cause slow system performance and affect running applications.

---

## Simulation

High disk I/O was generated using the `fio` tool.

Example command used:

fio --name=high-io-test --filename=testfile --size=1G --bs=4k --rw=randwrite --ioengine=libaio --iodepth=32 --runtime=60 --time_based --group_reporting

---

## Investigation

Disk I/O usage was monitored using:

iostat -x 1

This command displays disk activity and utilization.

The investigation showed that disk utilization increased significantly during the test.

---

## Resolution

The process generating high disk I/O was identified using:

ps aux | grep fio

The process was terminated using:

kill <PID>

Once the process stopped, disk activity returned to normal.

---

## Commands Used

| Command | Purpose |
|-------|-------|
| iostat | Monitor disk I/O usage |
| fio | Generate high disk I/O load |
| ps | Identify running processes |
| grep | Filter process output |
| kill | Stop the process |

