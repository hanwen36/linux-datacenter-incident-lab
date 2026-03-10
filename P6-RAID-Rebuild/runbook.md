# Runbook - RAID Degraded Incident

## Symptoms

Possible indicators of a RAID degraded state:

- RAID array reports degraded status
- One disk is missing or failed

Check RAID status:

cat /proc/mdstat

---

## Investigation

Identify degraded RAID arrays.

Example output:

[2/1] [_U]

This indicates one disk has failed or been removed.

---

## Resolution

Remove the failed disk:

mdadm /dev/md0 --remove /dev/loop1

Add a replacement disk:

mdadm /dev/md0 --add /dev/loop1

---

## Verification

Verify RAID status again:

cat /proc/mdstat

Expected result:

[UU]
