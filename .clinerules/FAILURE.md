# Offline AI Failure Handler

When implementation fails:

---

Step 1

Capture:

Task ID

Files

Timestamp

Error

Stack Trace

Reason

---

Step 2

Attempt automatic repair.

Maximum retries:

2

---

Step 3

If retries fail

Update:

history.json

metrics.json

current_task.json

Mark task failed.

---

Step 4

Never corrupt existing files.

Restore backups if necessary.

---

Step 5

Return:

Failure Summary

Root Cause

Suggested Fix

Files Involved

---

Never continue to another task.

Stop immediately.

