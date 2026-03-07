# Runbook – Inode Exhaustion

## Incident

System reports:

No space left on device

But disk space is still available.

---

## Investigation

Check disk usage:

df -h

If disk is not full, check inode usage:

df -i

If output shows:

IUse% = 100%

then the filesystem has run out of inodes.

---

## Identify Cause

Check number of files in the directory:

ls | wc -l

Large numbers of small files can exhaust inodes.

---

## Remediation

Remove unnecessary files:

rm file_*

---

## Verification

Confirm inode usage has recovered:

df -i

Expected result:

IUse% significantly reduced.

The system should now allow file creation.

---

## Prevention

Recommended practices:

• Monitor inode usage  
• Rotate logs regularly  
• Clean temporary directories
