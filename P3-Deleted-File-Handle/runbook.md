P3 runbook.md
# Runbook - Deleted File Handle Incident

## Symptoms

Possible indicators of a deleted file handle issue:

- Disk usage remains high after deleting a file
- Disk space is not released
- `df -h` still shows high usage

Check disk usage:

df -h

If disk usage remains high after deleting files, further investigation is required.

---

## Investigation

Identify processes holding deleted files:

lsof | grep deleted

Example output:

tail 1867 user ... big.log (deleted)

This indicates that a running process is still holding the deleted file.

---

## Resolution

Terminate the process holding the deleted file:

kill 1867

If the process does not stop:

kill -9 1867

Once the process stops, the disk space will be released.

---

## Verification

Verify disk usage again:

df -h

Expected result:

Disk space should return to normal.
