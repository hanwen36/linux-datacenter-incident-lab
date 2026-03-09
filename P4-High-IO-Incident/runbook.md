P4 runbook.md
# Runbook - High IO Incident

## Symptoms

Possible indicators of a high disk I/O issue:

- System performance becomes slow
- High disk utilization
- Monitoring tools report high I/O usage

Check disk activity:

iostat -x 1

If disk utilization is very high, further investigation is required.

---

## Investigation

Identify processes generating disk activity.

Check running processes:

ps aux | grep fio

Look for processes performing heavy disk operations.

---

## Resolution

Terminate the process causing high disk activity:

kill <PID>

If necessary:

kill -9 <PID>

---

## Verification

Verify disk activity has returned to normal:

iostat -x 1

Disk utilization should decrease after the process is stopped.
