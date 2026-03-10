# Triage Guide: Clipboard Data Collection

## Detection Title
Clipboard Data Collection

## Detection ID
SENT-COLL-0001

## Objective

This detection identifies command-line or PowerShell activity interacting with clipboard contents. This may indicate collection of copied data, credentials, tokens, or user-generated content from the local system.

## Why It Matters

Attackers may access clipboard data to capture:
- copied passwords
- MFA codes
- wallet addresses
- sensitive text copied from documents or portals
- other user data staged in memory for quick access

Clipboard access alone is not inherently malicious, but it becomes more concerning when combined with credential access, scripting, or outbound transfer behavior.

## Alert Logic Summary

The rule looks for:
- `powershell.exe`
- `pwsh.exe`
- `cmd.exe`

with command lines containing:
- `Get-Clipboard`
- `Set-Clipboard`
- `clip.exe`

## Initial Triage Questions

- Who ran the command?
- Was the user performing legitimate admin or scripting work?
- Was the command interactive, scripted, or part of automation?
- Did the same session show signs of credential access, staging, or exfiltration?
- Is the host a normal workstation, admin jump box, or shared support system?

## Investigation Steps

1. Review the full process command line.
2. Confirm the executing user and logon context.
3. Identify the parent process.
4. Determine whether the activity was initiated from:
   - an interactive terminal
   - a script
   - a remote session
   - an automation tool
5. Check for related activity shortly before or after:
   - archive creation
   - file enumeration
   - browser credential access
   - outbound network connections
6. Review whether the clipboard command was reading, overwriting, or piping data.

## Common False Positives

- benign PowerShell automation
- help desk or support workflows
- user productivity scripts
- clipboard cleanup or formatting utilities
- scripts that copy command output for administrative purposes

## Escalation Guidance

Escalate when:
- clipboard access is paired with suspicious scripting or encoded commands
- the affected user is privileged or high-value
- clipboard access occurs near exfiltration, archiving, or credential-theft behavior
- the parent process or execution context is suspicious
- the user cannot explain the activity

## Recommended Enrichment

- process tree
- user logon session context
- parent and child processes
- recent file access activity
- recent network connections
- related alerts on the same host
- account privilege level

## ATT&CK Mapping

- Collection
- T1115 – Clipboard Data

## Related Rule

- `detections/sentinel/collection/clipboard-data-collection.yml`
