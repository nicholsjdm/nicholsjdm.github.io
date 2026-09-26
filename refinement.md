---
title: Playbook Refinement
---

# Playbook refinement 

Windows endpoint IR playbook, version 1.4. Refined 26 Sep 2026 after peer review from a classmate.

I initially developed after a real incident response was completed at my work. I tested and modified PowerShell scripts on Windows 10 Pro. Supervisor review still pending. I am using a sanitized copy only which means no client names and no live IOCs.

## What changed after peer review

### Added isolate now vs collect first section
Default: one unknown foreign address is enough to isolate. Analyze from the backup image later.
Isolate immediately if there is unknown foreign C2, a keylogger or possible PII/PHI, or an active attacker.
Collect Stage 2 (Volatile Evidence) first only if the network edge already blocked the path (DNS or IP) and a supervisor agrees to wait minutes, not hours.

### Where evidence goes
`C:\IR_...` on the host is temporary. Zip and hash go to the approved share. Hash the copy, record who moved it, and delete the working copy on the endpoint. Read/Write permissions for IR techs on that ticket and the supervisor only.

### Other clients
A hash from Client A is not permission to browse Client B. Supervisor approval and a ticket on that customer first. Use MSP tools for network-wide threat hunt instead. 

### Test log
Win10 Pro test run passed (Stages 0–2). Win11 Pro and Server has not run until supervisor review. Each stage gets Completed / Failed / Skipped plus a reason.

### Ethics tied to the work
Scope stays on the compromise and on recovery the customer asked for. Explicitly stated not to use public sandboxes and no snooping.

## Impact
The next tech is not guessing when to isolate or where the zip lives or if they left it on the client machine. We trade some live telemetry for less time an attacker has on someone else's machine.
