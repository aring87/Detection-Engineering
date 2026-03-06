# Detection Engineering

A centralized repository for building, governing, validating, and reporting on a modern detection engineering program.

This repository is designed to serve as a one-stop location for:
- detection engineering strategy and program documentation
- executive proposal and maturity reporting
- detection-as-code content for Microsoft Sentinel
- ATT&CK and Cyber Kill Chain coverage tracking
- validation, tuning, and quality standards
- workflow automation and CI/CD foundations
- SOC workflow alignment and continuous improvement

---

## Purpose

Detection engineering is more than writing alert logic. A mature program requires structure, governance, testing, reporting, and a repeatable process for turning threat hypotheses into reliable security analytics.

This repository brings those pieces together in a single platform so the program can be managed like an engineering discipline rather than a loose collection of rules.

---

## Repository Objectives

This repository supports the full detection engineering lifecycle:

1. Define strategy and governance
2. Intake and prioritize detection opportunities
3. Build and maintain detections as code
4. Validate detections against real or simulated activity
5. Tune detections to improve fidelity and reduce noise
6. Deploy content through controlled workflows
7. Measure coverage, quality, and program maturity
8. Report value to SOC leadership and executive stakeholders

---

## Repository Structure

### Executive and program documentation
- `docs/00_executive/` — executive summary, proposal, charter, roadmap
- `docs/01_strategy/` — mission, scope, operating model, maturity model
- `docs/02_process/` — detection lifecycle, intake, QA, tuning, exceptions, change control
- `docs/03_visuals/` — diagrams and charts for leadership and engineering
- `docs/04_reporting/` — metrics catalog, quarterly reviews, gap analysis

### Governance
- `governance/` — naming, severity, lifecycle, tagging, and analytic quality standards

### Detection content
- `detections/sentinel/` — Microsoft Sentinel detection content
- `detections/mappings/` — ATT&CK and Cyber Kill Chain mappings
- `detections/sigma/` — Sigma content when applicable

### Reusable content
- `content/templates/` — templates for detections, requests, triage guides, and validation
- `content/runbooks/` — analyst and engineering operating guides
- `content/playbooks/` — automation and response content
- `content/workbooks/` — workbook-related content and standards

### Coverage and reporting
- `coverage/` — ATT&CK and Cyber Kill Chain coverage data, summaries, and gap tracking
- `dashboards/` — Sentinel workbooks and executive metrics content

### Automation and validation
- `automation/` — scripts, schemas, deployment helpers, reporting support
- `tests/` — validation references, sample logs, and testing support
- `.github/workflows/` — GitHub Actions for validation and deployment

---

## Current Focus

This repository is currently centered on **Microsoft Sentinel detection engineering**, while also being structured to expand into a broader multi-platform detection engineering program.

Planned future growth includes:
- Splunk detection engineering content
- standardized cross-platform detection metadata
- shared governance and lifecycle standards across tools
- common reporting and maturity tracking for multiple security platforms

---

## Detection Lifecycle

Each detection should move through a controlled lifecycle:

- `experimental`
- `testing`
- `production`
- `deprecated`

This lifecycle helps ensure detections are:
- documented
- reviewed
- validated
- tuned
- maintained over time

More detail is maintained in:
- `docs/02_process/detection-lifecycle.md`
- `governance/lifecycle-standard.md`

---

## Detection Content Standards

Each detection should include, where applicable:
- title
- unique identifier
- description
- author
- created and modified dates
- platform
- data sources
- ATT&CK tactic and technique mapping
- Cyber Kill Chain phase
- severity
- query or logic
- false-positive considerations
- triage guidance
- validation notes
- lifecycle state
- owner

Templates and guidance are located in:
- `content/templates/detection-rule-template.yml`
- `content/templates/rule-request-template.md`
- `content/templates/triage-guide-template.md`
- `content/templates/validation-checklist.md`

---

## Executive Value

This repository supports executive and leadership visibility by providing:
- a formal detection engineering proposal
- maturity model documentation
- ATT&CK coverage tracking
- gap analysis
- program visuals and workflow diagrams
- reporting structures for quarterly and annual review

Key leadership outcomes include:
- improved visibility into detection coverage
- measurable program maturity
- better prioritization of detection engineering efforts
- reduced analyst burden through more structured tuning and triage
- stronger alignment between SOC operations and engineering

---

## Primary Audiences

### Leadership
This repository provides strategy, executive summaries, maturity reporting, and measurable program outcomes.

### Detection Engineers
This repository provides standards, templates, detection content, mappings, validation guidance, and workflow structure.

### SOC Analysts and Incident Responders
This repository provides triage support, workflow alignment, coverage context, and a path for alert feedback and tuning.

---

## Microsoft Sentinel Content

The Sentinel portion of this repository is intended to support:
- ATT&CK-aligned detections
- lifecycle-based analytic management
- rule tuning and validation
- workbook/reporting alignment
- future CI/CD-driven deployment

This creates a foundation for moving from isolated analytic rules to a full Sentinel detection engineering program.

---

## Coverage and Metrics

Coverage tracking is maintained to help answer:
- which ATT&CK techniques are covered
- where detection gaps remain
- which tactics have the strongest content support
- where new engineering effort should be prioritized
- how the program is maturing over time

Coverage artifacts are maintained under:
- `coverage/mitre/`
- `coverage/cyber-kill-chain/`

---

## Contribution Model

All content should be managed through version control and reviewed before promotion.

Recommended contribution flow:
1. Submit a request, change, or new detection
2. Review for metadata completeness and quality
3. Validate logic and mapping
4. Document tuning and operational considerations
5. Merge through pull request review
6. Promote through lifecycle stages

Supporting files:
- `CONTRIBUTING.md`
- `.github/PULL_REQUEST_TEMPLATE.md`
- `.github/ISSUE_TEMPLATE/`

---

## Suggested Roadmap

### Near-term
- normalize all existing Sentinel detections into a common schema
- standardize tactic folder naming
- expand ATT&CK and Cyber Kill Chain mappings
- add triage guides and validation evidence
- improve executive and operational reporting

### Mid-term
- strengthen GitHub Actions validation
- add deployment automation for Sentinel content
- expand coverage reporting
- build out workbook and dashboard structure

### Long-term
- expand into Splunk detection engineering
- support cross-platform detection standards
- mature into a full engineering-driven security content program

---

## Getting Started

### For leadership
Start here:
- `docs/00_executive/`
- `docs/01_strategy/`
- `docs/04_reporting/`

### For engineers
Start here:
- `detections/sentinel/`
- `content/templates/`
- `governance/`
- `tests/`

### For SOC and IR
Start here:
- `docs/02_process/`
- `content/templates/triage-guide-template.md`
- `coverage/`

---

## Repository Status

This repository is actively being developed into a full detection engineering platform that combines:
- proposal and program strategy
- detection-as-code
- governance standards
- testing and tuning workflows
- executive reporting
- platform expansion planning

---

## License

Add your preferred license here.