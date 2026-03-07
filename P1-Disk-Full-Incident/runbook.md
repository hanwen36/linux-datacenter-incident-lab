Incident: Disk Full

Symptoms
System reports no space left on device.

Investigation
df -h
du -ah

Root Cause
Large files consumed disk space.

Resolution
Remove unnecessary files.

Prevention
Implement log rotation.
