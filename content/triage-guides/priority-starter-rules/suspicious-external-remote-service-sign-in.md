# Suspicious External Remote Service Sign-In

## Rule Metadata
- **Rule ID:** SENT-INIT-0002
- **Tactics:** Initial Access
- **Techniques:** T1133
- **Severity:** high
- **Data Sources:** SigninLogs
- **Lifecycle Target:** Move from `experimental` to `testing` after initial tuning and validation

## Detection Objective
Detects successful external sign-ins to remote access or administrative services that may represent abuse of external remote services.

## What the Detection Is Looking For
This analytic is intended to highlight behavior that can indicate attacker activity related to initial access. Review the triggering event in the broader context of the user, host, parent process, and surrounding activity.

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
- Authorized travel or remote administration
- Known VPN gateways or managed remote services

## Recommended Enrichment
- Parent and child process chain
- User account role and privilege level
- Device criticality or asset class
- Related alerts on the same host or user
- Nearby process, file, network, or sign-in events

## Rule-Specific Triage Guidance
- Review location, device, and identity risk context
- Compare to the user's baseline sign-in patterns
- Correlate with endpoint remote access events

## Validation Checklist
- [ ] Validate against known remote access scenarios in your environment

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
SigninLogs
| where ResultType == 0
| where IPAddress !startswith "10." and IPAddress !startswith "192.168."
| where AppDisplayName has_any ("Azure Portal","Windows Sign In","VPN","Remote Desktop")
| project TimeGenerated, UserPrincipalName, IPAddress, AppDisplayName, Location, ConditionalAccessStatus
```
