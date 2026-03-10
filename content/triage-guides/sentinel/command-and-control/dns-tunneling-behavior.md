# Triage Guide: DNS Tunneling Behavior

## Detection Title
DNS Tunneling Behavior

## Detection ID
SENT-C2-0001

## Objective

This detection identifies unusually high volumes of DNS traffic combined with long query lengths over a short time window. This may indicate DNS tunneling, covert beaconing, or encoded data transfer through DNS queries.

## Why It Matters

DNS tunneling can be used for:
- covert command-and-control
- data exfiltration
- persistence of communications when web traffic is restricted
- blending malicious traffic into commonly allowed DNS flows

High query counts plus long query strings are a useful signal for suspicious DNS abuse.

## Alert Logic Summary

The rule looks for:
- `DeviceNetworkEvents`
- DNS traffic on port 53
- summarized activity over 15 minutes
- high query counts
- elevated average DNS query length

## Initial Triage Questions

- Which process is generating the DNS traffic?
- Is the process normally DNS-heavy in this environment?
- Are the queries abnormally long, repetitive, or high-entropy?
- Does the traffic appear TXT-heavy or tunneling-like?
- Is there related process execution or staging behavior?

## Investigation Steps

1. Review the initiating process name and user context.
2. Confirm the host type and whether it normally generates heavy DNS traffic.
3. Examine query characteristics if available:
   - query length
   - domain patterns
   - repetition
   - entropy-like appearance
4. Review the 15-minute burst for volume and recurrence.
5. Check for known developer, security, or diagnostics tools that may explain the behavior.
6. Correlate with:
   - suspicious process execution
   - external downloads
   - archive creation
   - exfiltration-related activity

## Common False Positives

- developer tooling with frequent DNS lookups
- internal diagnostics or troubleshooting tools
- some security products or research tools
- misconfigured scripts repeatedly resolving domains

## Escalation Guidance

Escalate when:
- the generating process is unusual or suspicious
- domains or queries look encoded or tunneled
- activity is repeated across intervals
- the host also shows execution or staging behavior
- the user or host context makes the activity abnormal

## Recommended Enrichment

- destination domains if available
- DNS query lengths and frequency
- initiating process path and signer
- process tree
- related external network activity
- file staging or archive activity
- host role and criticality

## ATT&CK Mapping

- Command and Control
- T1071.004 – Application Layer Protocol: DNS

## Related Rule

- `detections/sentinel/command-and-control/dns-tunneling-behavior.yml`
