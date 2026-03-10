# Triage Guide: Suspicious Web Download via Certutil or Bitsadmin

## Detection Title
Suspicious Web Download via Certutil or Bitsadmin

## Detection ID
SENT-C2-0003

## Objective

This detection identifies use of built-in Windows utilities such as `certutil.exe` or `bitsadmin.exe` to download remote content. This may indicate staging of payloads, command-and-control tooling, or remote script retrieval.

## Why It Matters

Attackers commonly abuse Windows-native tools to:
- fetch payloads from remote infrastructure
- blend malicious activity into trusted system binaries
- avoid dropping custom downloaders
- stage follow-on execution using built-in utilities

Use of these tools for web downloads is a classic living-off-the-land technique.

## Alert Logic Summary

The rule looks for:
- `DeviceProcessEvents`
- `certutil.exe` or `bitsadmin.exe`
- command lines containing:
  - `http://`
  - `https://`
  - `/transfer`
  - `-urlcache`

## Initial Triage Questions

- Which tool was used?
- What URL or destination was referenced?
- Where was the file downloaded?
- Was the command part of approved admin or software-distribution activity?
- Was the downloaded content later executed?

## Investigation Steps

1. Review the full command line.
2. Extract and review the destination URL if present.
3. Identify the user, host, and parent process.
4. Determine the download location and whether the file still exists.
5. Check for subsequent behavior:
   - execution from temp or downloads
   - DLL or script execution
   - persistence changes
   - additional external connections
6. Determine whether the activity matches a known administrative workflow.

## Common False Positives

- approved software distribution tasks
- troubleshooting by administrators
- internal packaging or deployment scripts
- support engineers downloading known-good utilities

## Escalation Guidance

Escalate when:
- the URL is suspicious or unfamiliar
- the downloaded content is executed soon after
- the parent process or user context is unusual
- the download is directed to suspicious paths
- the activity is paired with persistence, staging, or outbound callbacks

## Recommended Enrichment

- full command line
- URL/domain reputation
- downloaded file path
- file hash and signer status
- parent and child processes
- related network activity
- recent alerts on the same device

## ATT&CK Mapping

- Command and Control
- Execution
- T1105 – Ingress Tool Transfer

## Related Rule

- `detections/sentinel/command-and-control/suspicious-web-download-via-certutil-or-bitsadmin.yml`
