# Sentinel Detection Starter Rules Pack

This pack includes 42 starter Microsoft Sentinel detections organized across 14 ATT&CK tactic-aligned folders, with 3 rules per folder.

Important notes:
- These are starter detections intended to seed your repository and accelerate backlog development.
- They use a normalized YAML schema consistent with your current repo direction.
- Queries are written primarily for Microsoft Defender XDR / Sentinel tables such as DeviceProcessEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceNetworkEvents, SigninLogs, AuditLogs, OfficeActivity, UrlClickEvents, IdentityLogonEvents, and CloudAppEvents.
- Validate field names, table availability, and thresholds in your environment before promoting any rule beyond experimental.
