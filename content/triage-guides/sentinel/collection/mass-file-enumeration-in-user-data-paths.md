# Triage Guide: Mass File Enumeration in User Data Paths

## Detection Title
Mass File Enumeration in User Data Paths

## Detection ID
SENT-COLL-0002

## Objective

This detection identifies processes touching large numbers of files across user data paths within a short period. This may indicate data discovery, staging, or collection activity prior to archiving or exfiltration.

## Why It Matters

Large-scale file enumeration across:
- user profiles
- desktop folders
- document folders
- download directories

can indicate an attempt to identify or collect valuable user data. While some legitimate tools do this, the behavior is important to review when tied to suspicious processes or timing.

## Alert Logic Summary

The rule looks for activity in paths such as:
- `\Users\`
- `\Desktop\`
- `\Documents\`
- `\Downloads\`

It summarizes file touches over 15 minutes and alerts when:
- file touches are high
- multiple distinct user-data paths are involved

## Initial Triage Questions

- What process touched the files?
- Is the process a known backup, indexing, or security tool?
- Was the user performing normal file-management activity?
- Did the process also create archives or stage files?
- Is there outbound transfer behavior soon after?

## Investigation Steps

1. Identify the initiating process and account.
2. Review the time window and total file-touch volume.
3. Confirm whether the process is expected on the host.
4. Determine whether the activity is:
   - backup
   - search indexing
   - anti-malware scanning
   - scripted file collection
5. Review for related activity after enumeration:
   - zip or archive creation
   - cloud upload
   - external network transfer
   - copying to temporary or staging locations
6. Check whether the same process touched sensitive departments, shared data, or multiple users’ folders.

## Common False Positives

- backup agents
- indexing services
- anti-malware or EDR scanning
- administrative bulk file operations
- migration or profile-copy utilities

## Escalation Guidance

Escalate when:
- the process is unusual or unsigned
- enumeration is followed by compression or transfer
- the user context is suspicious
- the process is script-based or attacker-adjacent
- the host shows related discovery, collection, or exfiltration behavior

## Recommended Enrichment

- initiating process details
- signer and file path of the process
- parent process
- archive creation events
- outbound network telemetry
- cloud application activity
- recent alerts on the same host

## ATT&CK Mapping

- Collection
- T1005 – Data from Local System
- T1039 – Data from Network Shared Drive

## Related Rule

- `detections/sentinel/collection/mass-file-enumeration-in-user-data-paths.yml`
