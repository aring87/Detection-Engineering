# Volume Shadow Copy Deletion

## Rule Metadata
- **Rule ID:** SENT-IMPACT-0001
- **Tactics:** Impact
- **Techniques:** T1490
- **Severity:** high
- **Data Sources:** DeviceProcessEvents
- **Lifecycle Target:** Move from `experimental` to `testing` after initial tuning and validation

## Detection Objective
Detects deletion of shadow copies using built-in Windows utilities, a common ransomware precursor.

## What the Detection Is Looking For
This analytic is intended to highlight behavior that can indicate attacker activity related to impact. Review the triggering event in the broader context of the user, host, parent process, and surrounding activity.

## Initial Triage Questions
- Who triggered the alert, and is that user expected to perform this activity?
- On what host did the alert occur, and is the host role consistent with the behavior?
- What process lineage, authentication context, or network activity is associated with the event?
- Is the event part of known administrative, deployment, or security tooling?

## Investigation Steps
1. Review the raw event and confirm the key fields used by the rule are populated correctly.
2. Validate the user, device, and parent process context.
3. Determine whether the activity aligns with known-good administration or sanctioned security tooling.
4. Review related process, file, registry, sign-in, or network activity before and after the alert.
5. Decide whether the event should be documented as a false positive, tuned, or escalated.

## Common False Positives
- Approved backup maintenance or restore workflows
- Lab validation or recovery testing

## Recommended Enrichment
- Parent and child process chain
- User account role and privilege level
- Device criticality or asset class
- Related alerts on the same host or user
- Nearby process, file, network, or sign-in events

## Rule-Specific Triage Guidance
- Validate whether the deletion was authorized
- Check for concurrent encryption or log clearing activity
- Inspect the parent process and user context

## Validation Checklist
- [ ] Delete shadow copies on a lab machine or replay representative telemetry

## Tuning Notes
- Confirm all field names and tables align with your Sentinel environment.
- Review 7 to 30 days of historical results before changing lifecycle.
- Document known-good tools, service accounts, hosts, and parent processes.
- Only suppress activity when the justification is durable and documented.

## Analyst Notes
- Status:
- Escalated to IR:
- False positive pattern:
- Tuning recommendation:
- Follow-up owner:

## Current Query
```kql
DeviceProcessEvents
| where FileName in~ ("vssadmin.exe","wmic.exe","powershell.exe")
| where ProcessCommandLine has_any ("delete shadows","shadowcopy delete","Win32_Shadowcopy")
| project Timestamp, DeviceName, AccountName, FileName, ProcessCommandLine
```
