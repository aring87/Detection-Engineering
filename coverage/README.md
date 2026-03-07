# Coverage

This directory contains coverage-tracking artifacts used to measure, visualize, and prioritize detection engineering progress.

## Purpose

Coverage tracking helps the program understand:
- which attacker behaviors are represented in current content
- where meaningful detection gaps remain
- which tactics or techniques need additional engineering focus
- how detection engineering maturity is progressing over time

Coverage is intended to support both engineering decision-making and leadership reporting.

## Coverage Areas

### MITRE ATT&CK
- [MITRE Folder](mitre/)

Used for:
- ATT&CK coverage matrices
- coverage summaries
- documented gaps
- gap closure tracking

### Cyber Kill Chain
- [Cyber Kill Chain Folder](cyber-kill-chain/)

Used for:
- CKC-aligned coverage views
- supporting summaries
- visual or matrix-based reporting where applicable

## Typical Artifacts

Examples of artifacts in this directory may include:
- coverage matrix CSV files
- coverage summary markdown files
- gap tracking documents
- supporting charts or exported visuals
- tactic and technique mapping support files

## How Coverage Should Be Used

Coverage artifacts should help answer questions such as:
- which ATT&CK tactics have the strongest current support?
- which tactics or techniques are underrepresented?
- which gaps are blocked by telemetry rather than engineering effort?
- which areas should be prioritized in the roadmap?
- how is coverage changing over time?

## Coverage Principles

Coverage tracking should be:

### Useful
It should support decision-making, not just exist as a count of mapped rules.

### Structured
Artifacts should be maintained in predictable folders and formats.

### Honest
Coverage should not overstate maturity or depth simply because a tactic has one starter rule.

### Aligned
Coverage should connect back to roadmap priorities, telemetry reality, and program maturity.

### Reportable
Artifacts should be usable in quarterly reviews, annual reviews, and executive updates.

## Related Content

- [Detections](../detections/)
- [Reporting](../docs/04_reporting/)
- [Strategy](../docs/01_strategy/)
- [Visuals](../docs/03_visuals/)
- [Data Source Catalog](../governance/data-source-catalog.md)

## Recommended Review Rhythm

Coverage artifacts should be reviewed:
- periodically during content expansion
- during quarterly reporting cycles
- during annual roadmap review
- whenever significant new detections are added
- whenever major telemetry changes affect use case feasibility

## Goal

The goal of this directory is to make detection coverage visible, actionable, and measurable so the program can mature deliberately rather than grow without direction.