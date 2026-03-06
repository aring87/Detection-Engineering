# Registry Run Key Modification

## Rule Metadata
- **Rule ID:** SENT-PERS-0001
- **Tactics:** Persistence
- **Techniques:** T1547.001
- **Severity:** high
- **Data Sources:** DeviceRegistryEvents
- **Lifecycle Target:** Move from `experimental` to `testing` after initial tuning and validation

## Detection Objective
Detects creation or modification of common autorun registry keys used for persistence.

## What the Detection Is Looking For
This analytic is intended to highlight behavior that can indicate attacker activity related to persistence. Review the triggering event in the broader context of the user, host, parent process, and surrounding activity.

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
- Legitimate software installers or updaters
- Authorized enterprise startup configuration changes

## Recommended Enrichment
- Parent and child process chain
- User account role and privilege level
- Device criticality or asset class
- Related alerts on the same host or user
- Nearby process, file, network, or sign-in events

## Rule-Specific Triage Guidance
- Review the written value and executable path
- Determine whether the initiating process is expected
- Check for associated file writes or scheduled task creation

## Validation Checklist
- [ ] Set a benign Run key in a lab and confirm the event triggers

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
DeviceRegistryEvents
| where RegistryKey has_any (
    @"\Software\Microsoft\Windows\CurrentVersion\Run",
    @"\Software\Microsoft\Windows\CurrentVersion\RunOnce",
    @"\Software\WOW6432Node\Microsoft\Windows\CurrentVersion\Run")
| where ActionType in~ ("RegistryValueSet","RegistryKeyCreated")
| project Timestamp, DeviceName, InitiatingProcessAccountName, InitiatingProcessFileName, RegistryKey, RegistryValueData
```
