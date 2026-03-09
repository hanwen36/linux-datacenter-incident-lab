# Runbook - Inode Full Incident

## Symptoms

Possible indicators of an inode exhaustion issue:

- Error: `No space left on device`
- New files cannot be created
- Disk space appears available

Check inode usage:


df -i


If inode usage is near 100%, further investigation is required.

---

## Investigation

Identify directories consuming large numbers of inodes:


du --inodes -d 2 | sort -nr | head


Example result:


117 ./smallfiles


This indicates a directory containing a large number of small files.

---

## Remediation

Remove unnecessary files:


rm -rf smallfiles


Recheck inode usage:


df -i


---

## Verification

Verify inode availability:


df -i


Expected result:


IUse% significantly reduced


---

## Evidence

terminal.log

screenshots/
