# DNS Tunneling Behavior

## Rule Metadata
- **Rule ID:** SENT-C2-0001
- **Tactics:** Command and Control
- **Techniques:** T1071.004
- **Severity:** high
- **Data Sources:** DeviceNetworkEvents
- **Lifecycle Target:** Move from `experimental` to `testing` after initial tuning and validation

## Detection Objective
Detects excessive or unusually long DNS query patterns that may represent DNS tunneling or beaconing.

## What the Detection Is Looking For
This analytic is intended to highlight behavior that can indicate attacker activity related to command and control. Review the triggering event in the broader context of the user, host, parent process, and surrounding activity.

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
- DNS-heavy developer or security tools
- Internal diagnostics generating repetitive lookups

## Recommended Enrichment
- Parent and child process chain
- User account role and privilege level
- Device criticality or asset class
- Related alerts on the same host or user
- Nearby process, file, network, or sign-in events

## Rule-Specific Triage Guidance
- Review the process generating the DNS traffic
- Determine whether the queried domains or lengths are abnormal
- Check for TXT-heavy or high-entropy query behavior

## Validation Checklist
- [ ] Replay DNS tunneling lab traffic or generate long repetitive queries

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
DeviceNetworkEvents
| where RemotePort == 53
| extend QueryLength = strlen(RemoteUrl)
| summarize QueryCount=count(), AvgQueryLength=avg(QueryLength) by DeviceName, InitiatingProcessFileName, bin(Timestamp, 15m)
| where QueryCount >= 100 and AvgQueryLength >= 40
```
