# Triage Guide: External PowerShell or LOLBin Traffic

## Detection Title
External PowerShell or LOLBin Traffic

## Detection ID
dodea-sig-020-external-powershell-LOLBIN-traffic

## Objective

This detection identifies outbound connections to public IP space from PowerShell or common LOLBins such as `wscript.exe` and `mshta.exe`. This may indicate remote payload retrieval, callback traffic, or abuse of native Windows tooling for command-and-control.

## Why It Matters

PowerShell and LOLBins are commonly used to:
- download remote payloads
- execute scripts from the internet
- establish outbound callbacks
- proxy malicious traffic through trusted native binaries

External traffic from these tools is not always malicious, but it is high value for triage.

## Alert Logic Summary

The rule looks for:
- `DeviceNetworkEvents`
- `RemoteIPType == "Public"`
- initiating process names:
  - `powershell.exe`
  - `wscript.exe`
  - `mshta.exe`

## Initial Triage Questions

- What process made the external connection?
- Was the process launched interactively, by script, or by another binary?
- Is the destination known and expected?
- Was the user performing legitimate admin or automation work?
- Did the process also execute suspicious commands, downloads, or script content?

## Investigation Steps

1. Review the initiating process and full command line if available in related telemetry.
2. Identify the user, parent process, and execution chain.
3. Review the destination:
   - IP
   - domain if available
   - reputation
   - geolocation if relevant
4. Determine whether the connection aligns with:
   - approved automation
   - software update behavior
   - expected admin scripting
5. Check for nearby suspicious events:
   - web downloads
   - encoded commands
   - child process launches
   - file writes to temp or user paths
6. Review recurrence across the same host or account.

## Common False Positives

- administrative scripts reaching public services
- support tooling using PowerShell or HTA frameworks
- approved software bootstrap or update activity
- scripted access to cloud APIs or public repos

## Escalation Guidance

Escalate when:
- the external destination is suspicious or unknown
- the process lineage is unusual
- the tool is launched from user-writable paths or script hosts
- there is follow-on execution, staging, or persistence
- the user cannot explain the activity

## Recommended Enrichment

- full command line
- parent and child processes
- destination IP/domain details
- file writes near the connection time
- script block or PowerShell telemetry if available
- related alerts on the same host
- user role and host sensitivity

## ATT&CK Mapping

- Command and Control
- T1071.001 – Application Layer Protocol: Web Protocols

## Related Rule

- `detections/sentinel/command-and-control/external-powershell-or-lolbin-traffic.yml`
