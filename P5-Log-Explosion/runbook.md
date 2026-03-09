# Runbook - Log Explosion Incident

## Symptoms

Possible indicators of a log explosion issue:

- Rapid disk space consumption
- Large log files
- Applications writing repeated error messages

Check disk usage:

df -h

If disk usage increases quickly, further investigation is required.

---

## Investigation

Identify large files on the system:

du -sh *

Look for unusually large log files.

Example output:

61G app.log

---

## Resolution

Clear the log file:

truncate -s 0 app.log

This removes the log content while keeping the file.

---

## Verification

Verify disk usage has returned to normal:

df -h

Disk usage should decrease after clearing the log file.
