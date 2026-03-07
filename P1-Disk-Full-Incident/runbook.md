# Runbook – Disk Full Incident

## Incident

System reports the error:

No space left on device

Applications may fail to write logs or create files.

---

## Investigation

Check disk usage:

df -h

If disk usage is close to 100%, the system may be out of disk space.

---

## Identify Cause

Locate large files consuming disk space:

du -ah . | sort -rh | head

Example output:

19G ./bigfile1  
2.1G ./bigfile2  
1.1G ./triggerfile

These files consumed nearly all disk capacity.

---

## Remediation

Remove unnecessary large files:

rm bigfile1 bigfile2 triggerfile

---

## Verification

Verify disk space has recovered:

df -h

Expected result:

Disk usage significantly reduced.

---

## Prevention

Recommended practices:

• Monitor disk usage regularly  
• Rotate logs using logrotate  
• Set disk usage alerts  
• Clean unused large files
