# Sentinel Detection Engineering

A centralized repository for building, governing, testing, deploying, and reporting on a modern detection engineering program in Microsoft Sentinel.

This repository is designed to be a one-stop location for:
- Detection engineering strategy and program documentation
- Executive proposal and maturity reporting
- Detection-as-code content for Microsoft Sentinel
- MITRE ATT&CK and Cyber Kill Chain coverage tracking
- Validation, tuning, testing, and QA standards
- CI/CD workflows for detection deployment
- SOC workflow alignment and continuous improvement

## Repository Objectives

This repository supports the full detection engineering lifecycle:
1. Define strategy and governance
2. Intake and prioritize detection opportunities
3. Build and maintain detections as code
4. Validate detections against real or simulated activity
5. Tune detections to reduce noise and increase fidelity
6. Deploy detections through controlled CI/CD workflows
7. Measure ATT&CK coverage, quality, and program maturity
8. Report value to SOC leadership and executive stakeholders

## Repository Layout

### Executive and program documentation
- `docs/00_executive/` — proposals, executive summary, charter, roadmap
- `docs/01_strategy/` — mission, scope, operating model, maturity model
- `docs/02_process/` — lifecycle, intake, QA, tuning, exceptions, change control
- `docs/04_reporting/` — metrics, quarterly reviews, gap analysis

### Governance
- `governance/` — naming, severity, lifecycle, tagging, data source, and quality standards

### Detection content
- `detections/sentinel/` — production and developing Sentinel analytics organized by ATT&CK tactic
- `detections/sigma/` — Sigma rules where applicable
- `detections/mappings/` — ATT&CK and Cyber Kill Chain mappings

### Reusable content
- `content/templates/` — templates for detections, requests, triage guides, and validation
- `content/runbooks/` — analyst and engineering operating guides
- `content/playbooks/` — response and automation content
- `content/workbooks/` — workbook standards and templates

### Testing and validation
- `tests/` — validation datasets, test harnesses, Atomic Red Team support, and sample logs

### Coverage and reporting
- `coverage/` — ATT&CK and Cyber Kill Chain coverage matrices, summaries, and detection gaps
- `dashboards/` — Sentinel workbooks and leadership metrics outputs

### Automation
- `automation/` — scripts, schemas, deployment content, and reporting helpers
- `.github/workflows/` — validation and deployment automation

## Detection Lifecycle

Each detection should move through a controlled lifecycle:
- `experimental`
- `testing`
- `production`
- `deprecated`

## Rule Requirements

Every detection should include:
- Title
- Unique ID
- Status
- Description
- Author
- Date created / modified
- Data source(s)
- ATT&CK tactic and technique
- Cyber Kill Chain phase
- Severity
- Query or logic
- False positives
- Validation notes
- Triage guidance
- Lifecycle state

## Primary Audiences

### Leadership
This repo provides executive summaries, maturity reporting, roadmap tracking, and measurable coverage outcomes.

### Detection Engineers
This repo provides templates, standards, rule content, validation patterns, automation, and deployment workflows.

### SOC Analysts and Incident Responders
This repo provides triage guidance, workflow alignment, and feedback mechanisms to improve alert quality over time.

## Recommended Initial Priorities

1. Add the detection engineering proposal and executive summary
2. Normalize rule schema for all Sentinel detections
3. Build out lifecycle and intake process documents
4. Add ATT&CK coverage matrix and gap analysis
5. Implement validation workflow in GitHub Actions
6. Add triage guide templates for analysts
7. Add a quarterly reporting template for leadership
