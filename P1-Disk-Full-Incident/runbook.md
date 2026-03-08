# Runbook - Disk Full Incident

## Symptoms

Possible indicators of a disk full incident:

- Error message: `No space left on device`
- Applications cannot write logs
- System services fail to start
- High disk usage reported by monitoring tools

Check disk usage:


df -h


If disk usage is near 100%, further investigation is required.

---

## Investigation

Identify directories or files consuming disk space:


du -ah . | sort -rh | head


Look for:

- large log files
- temporary files
- unexpected data growth

Example output:


19G ./bigfile1
2.1G ./bigfile2
1.1G ./triggerfile


---

## Remediation

Remove unnecessary large files:


rm bigfile1 bigfile2 triggerfile


Recheck disk usage:


df -h


Confirm that disk space has been released.

---

## Verification

Verify system health:


df -h


Expected result:

Disk usage should return to normal levels.

---


