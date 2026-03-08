# Runbook – Disk Full Incident

## Part 1 – Symptoms and Detection

A disk full condition may cause the following issues:

No space left on device

Applications may fail to write logs or create files.

Check disk usage with:

df -h

If disk usage is close to 100%, the system may be out of disk space.

---

## Part 2 – Investigation and Remediation

Locate the largest files on the system:

du -ah . | sort -rh | head

This command lists the largest files and helps identify what is consuming disk space.

Example output:

19G ./bigfile1  
2.1G ./bigfile2  
1.1G ./triggerfile  

Remove unnecessary large files:

rm bigfile1 bigfile2 triggerfile

Verify disk usage has returned to normal:

df -h

---

## Prevention

Recommended practices:

• Monitor disk usage regularly  
• Configure disk usage alerts  
• Implement log rotation using logrotate  
• Remove unused large files
