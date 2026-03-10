# Triage Guide: DNS Tunneling Using Iodine

## Detection Title
DNS Tunneling Using Iodine

## Detection ID
dodea-sig-033-dns-tunnel-iodine

## Objective

This detection identifies network connections over DNS port 53 from a process associated with Iodine, a known DNS tunneling tool. This may indicate covert command-and-control or data transfer using DNS as a transport mechanism.

## Why It Matters

DNS tunneling tools such as Iodine can be used to:
- bypass network controls
- establish covert command-and-control
- move data through DNS traffic
- hide malicious communications in a commonly allowed protocol

Use of Iodine on an endpoint is rarely normal in enterprise environments.

## Alert Logic Summary

The rule looks for:
- `DeviceNetworkEvents`
- `RemotePort == 53`
- `InitiatingProcessFileName` containing `iodine`

## Initial Triage Questions

- Is Iodine approved or expected in this environment?
- Which user executed the process?
- Is the host a workstation, server, or test system?
- Were there repeated DNS connections or sustained traffic?
- Is there related suspicious process, archive, or exfiltration behavior?

## Investigation Steps

1. Review the initiating process name, path, and user context.
2. Confirm whether the file is actually Iodine or similarly named masquerading content.
3. Check the parent process and execution lineage.
4. Review the timeline of DNS activity:
   - duration
   - frequency
   - destination patterns
5. Determine whether the host also shows:
   - encoded command execution
   - archive creation
   - file staging
   - unusual external traffic
6. Review whether the host role makes any legitimate tunneling activity plausible.

## Common False Positives

- lab or red team testing using Iodine
- controlled security validation exercises
- research systems intentionally running DNS tunnel tools

## Escalation Guidance

Escalate when:
- Iodine execution is not explicitly authorized
- DNS activity is sustained or repetitive
- the host also shows staging, execution, or exfiltration behavior
- the tool is executed from suspicious paths or by unusual accounts
- the user cannot explain the activity

## Recommended Enrichment

- full process path
- file hash and signer status
- parent process
- DNS request volume and timing
- queried domains if available
- related file, process, and network activity
- host criticality and user role

## ATT&CK Mapping

- Command and Control
- T1071.004 – Application Layer Protocol: DNS

## Related Rule

- `detections/sentinel/command-and-control/dns-tunneling-using-iodine.yml`
