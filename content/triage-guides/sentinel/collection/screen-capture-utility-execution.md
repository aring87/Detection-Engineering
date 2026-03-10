# Triage Guide: Screen Capture Utility Execution

## Detection Title
Screen Capture Utility Execution

## Detection ID
SENT-COLL-0003

## Objective

This detection identifies execution of screenshot or screen-capture tools that may be used to collect visible user-session data, application contents, or on-screen credentials.

## Why It Matters

Screen capture can be used to collect:
- user session details
- visible documents
- internal dashboards
- chat contents
- credentials or MFA prompts displayed on screen

This behavior is not always malicious, but it becomes more significant when tied to remote access, credential theft, or exfiltration activity.

## Alert Logic Summary

The rule looks for execution of:
- `snippingtool.exe`
- `psr.exe`
- `nircmd.exe`

or command lines containing:
- `screenshot`
- `capturedesktop`
- `screen capture`

## Initial Triage Questions

- Was the host being used for support or documentation?
- Is the user known to take screenshots as part of their role?
- Was the tool launched interactively or by script?
- Were image files written to disk?
- Was there follow-on staging or exfiltration behavior?

## Investigation Steps

1. Review the executing process and command line.
2. Identify the user and session context.
3. Determine whether the host was under support, training, or documentation activity.
4. Review whether image or capture files were created and where.
5. Check for related suspicious activity:
   - remote access tools
   - credential access
   - archive creation
   - outbound transfer
6. Determine whether the tool is approved and expected in the environment.

## Common False Positives

- legitimate screenshots by users
- IT support sessions
- training or documentation creation
- problem-step recording for troubleshooting
- approved admin or automation tooling

## Escalation Guidance

Escalate when:
- capture tools are launched by unusual parent processes
- capture activity is scripted or hidden
- images are staged for outbound transfer
- the affected host or account is high-value
- the activity is paired with credential access or remote-control behavior

## Recommended Enrichment

- process tree
- written image or recording files
- destination folders
- recent outbound network activity
- remote access tool presence
- related alerts on the same host
- user role and host sensitivity

## ATT&CK Mapping

- Collection
- T1113 – Screen Capture

## Related Rule

- `detections/sentinel/collection/screen-capture-utility-execution.yml`
