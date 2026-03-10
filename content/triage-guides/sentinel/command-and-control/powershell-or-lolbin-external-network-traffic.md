# Triage Guide: PowerShell or LOLBin External Network Traffic

## Detection Title
PowerShell or LOLBin External Network Traffic

## Detection ID
SENT-C2-0002

## Objective

This detection identifies outbound connections to external destinations from PowerShell and common LOLBins such as `mshta.exe`, `rundll32.exe`, `regsvr32.exe`, and `certutil.exe`. This may indicate payload retrieval, callback traffic, or remote content execution.

## Why It Matters

Adversaries frequently use built-in tools to:
- contact remote infrastructure
- fetch scripts or payloads
- proxy malicious traffic through trusted binaries
- establish command-and-control

These binaries have legitimate uses, but external network activity from them is often worth investigating.

## Alert Logic Summary

The rule looks for:
- `DeviceNetworkEvents`
- initiating processes:
  - `powershell.exe`
  - `pwsh.exe`
  - `mshta.exe`
  - `rundll32.exe`
  - `regsvr32.exe`
  - `certutil.exe`
- remote IPs outside private address ranges

## Initial Triage Questions

- Which binary made the connection?
- What launched it?
- Is the external destination expected?
- Was this a download, callback, or one-off connection?
- Are there follow-on execution or persistence events?

## Investigation Steps

1. Review the initiating process and account context.
2. Check the parent process and surrounding execution chain.
3. Review the destination IP, domain, and port.
4. Determine whether the tool normally talks externally in this environment.
5. Look for nearby activity such as:
   - downloads
   - temp-file writes
   - DLL/script execution
   - persistence creation
6. Assess whether the external connection occurred on a privileged host, server, or admin account.

## Common False Positives

- approved admin automation
- software installation or update workflows
- security or compliance scripts
- support tools using public services

## Escalation Guidance

Escalate when:
- the destination is suspicious or unrecognized
- the process is spawned by unusual parents
- the same host shows multiple suspicious LOLBin executions
- there is evidence of staging or follow-on execution
- the activity involves privileged users or critical systems

## Recommended Enrichment

- full command line
- parent and child processes
- destination domain/IP reputation
- related file events
- script or DLL load telemetry if available
- recent alerts on the device
- host criticality and user context

## ATT&CK Mapping

- Command and Control
- Execution
- T1105 – Ingress Tool Transfer
- T1218 – System Binary Proxy Execution

## Related Rule

- `detections/sentinel/command-and-control/powershell-or-lolbin-external-network-traffic.yml`
