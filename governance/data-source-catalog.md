# Data Source Catalog

## Purpose

This catalog provides a high-level reference for the major telemetry sources used to support detection engineering content.

The goal is to help engineers, analysts, and reviewers understand which data sources are available, what behaviors they support, and where telemetry gaps may affect detection coverage.

---

## Catalog Goals

This catalog is intended to:
- map detections to real telemetry sources
- improve visibility into available log tables
- support ATT&CK coverage planning
- identify content dependencies
- document gaps and assumptions
- help prioritize new data source onboarding

---

## Recommended Data Source Attributes

Each data source entry should describe:
- source name
- platform or product
- primary use cases
- common ATT&CK tactics supported
- limitations or caveats
- related detection content

---

## Microsoft Sentinel / Defender-Oriented Data Sources

### DeviceProcessEvents
**Purpose:**  
Process execution telemetry for endpoints.

**Supports:**  
- execution
- defense evasion
- discovery
- lateral movement
- credential access
- impact

**Common Use Cases:**  
- PowerShell abuse
- LOLBin usage
- suspicious command-line arguments
- process ancestry analysis
- ransomware preparation behavior

**Notes:**  
One of the most important endpoint detection tables for behavior-based analytics.

---

### DeviceFileEvents
**Purpose:**  
File creation, modification, rename, and deletion activity on endpoints.

**Supports:**  
- execution
- persistence
- collection
- impact
- exfiltration preparation

**Common Use Cases:**  
- script drops
- staging behavior
- suspicious archive creation
- temp path usage
- destructive file actions

**Notes:**  
Useful when paired with process telemetry for context.

---

### DeviceNetworkEvents
**Purpose:**  
Network connection telemetry from endpoints.

**Supports:**  
- command and control
- exfiltration
- discovery
- initial access
- lateral movement

**Common Use Cases:**  
- rare outbound destinations
- suspicious ports
- beaconing patterns
- remote service access
- unexpected internet communication

**Notes:**  
Often most useful when correlated with process telemetry.

---

### DeviceRegistryEvents
**Purpose:**  
Registry modification telemetry from endpoints.

**Supports:**  
- persistence
- defense evasion
- privilege escalation

**Common Use Cases:**  
- run key persistence
- security setting modification
- autorun abuse
- configuration tampering

**Notes:**  
High-value source for persistence analytics.

---

### DeviceLogonEvents
**Purpose:**  
Endpoint logon activity.

**Supports:**  
- credential access
- lateral movement
- privilege escalation
- initial access

**Common Use Cases:**  
- unusual logon types
- admin account usage
- failed logon bursts
- suspicious remote logons

**Notes:**  
Helpful for identity + endpoint correlation.

---

### SigninLogs
**Purpose:**  
Azure AD / Entra ID sign-in telemetry.

**Supports:**  
- initial access
- persistence
- credential access
- defense evasion

**Common Use Cases:**  
- suspicious sign-ins
- device code abuse
- impossible travel
- rare countries
- MFA anomalies
- unfamiliar application access

**Notes:**  
Critical for identity-focused detections.

---

### AuditLogs
**Purpose:**  
Cloud administrative and directory activity.

**Supports:**  
- persistence
- privilege escalation
- resource development
- defense evasion

**Common Use Cases:**  
- application registration
- role assignment
- policy changes
- mailbox rule creation
- admin setting modifications

**Notes:**  
High-value source for cloud control-plane monitoring.

---

### IdentityDirectoryEvents
**Purpose:**  
Directory and identity-related events.

**Supports:**  
- discovery
- credential access
- persistence
- privilege escalation

**Common Use Cases:**  
- directory enumeration
- identity object changes
- account management activity
- suspicious identity operations

**Notes:**  
Useful when combined with audit and sign-in telemetry.

---

### CloudAppEvents
**Purpose:**  
Cloud application activity.

**Supports:**  
- exfiltration
- collection
- resource development
- defense evasion

**Common Use Cases:**  
- bulk uploads
- file sharing anomalies
- app-specific suspicious behavior
- unusual cloud access patterns

**Notes:**  
Important for SaaS and insider-risk style detections.

---

### SecurityEvent
**Purpose:**  
Windows security event log data.

**Supports:**  
- credential access
- persistence
- privilege escalation
- lateral movement
- discovery

**Common Use Cases:**  
- account logon activity
- service creation
- scheduled tasks
- group membership changes
- authentication anomalies

**Notes:**  
Often useful in hybrid or legacy Windows visibility scenarios.

---

## Additional Catalog Expansion Areas

Future entries may include:
- Sysmon-based telemetry
- DNS logs
- firewall logs
- email security telemetry
- proxy logs
- AzureActivity
- AzureDiagnostics
- AADServicePrincipalSignInLogs
- custom application logs
- watchlists and enrichment data sources

---

## Catalog Usage

This catalog should be used during:
- detection design
- use case prioritization
- ATT&CK coverage planning
- rule reviews
- gap analysis
- roadmap development

---

## Gap Tracking

When a desired use case cannot be supported, document:
- required data source
- current availability status
- blocking dependency
- workaround if any
- roadmap priority

This helps distinguish between:
- engineering gaps
- telemetry gaps
- process gaps

---

## Recommended Future Enhancements

Over time, this catalog can be expanded to include:
- table owners
- ingestion status
- retention notes
- field quality observations
- key columns per table
- linked detections by data source
- detection counts per source

---

## Summary

A strong data source catalog improves the quality of detection engineering by grounding content in real telemetry, clarifying dependencies, and making coverage planning more deliberate and transparent.