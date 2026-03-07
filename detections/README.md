# Detections

This directory contains detection content managed as code.

## Structure

### Sentinel
- [Sentinel Folder](sentinel/)

Microsoft Sentinel detections are organized by ATT&CK tactic-aligned folders.

### Sigma
- [Sigma Folder](sigma/)

Reserved for Sigma content where applicable.

### Mappings
- [Mappings Folder](mappings/)

Used for ATT&CK and Cyber Kill Chain mapping artifacts.

## Detection Expectations

Detection content should follow repository standards for:
- naming
- lifecycle
- severity
- tagging
- metadata quality
- folder placement

See:
- [Governance](../governance/)
- [Detection Rule Template](../content/templates/detection-rule-template.yml)
- [QA and Validation Standard](../docs/02_process/qa-validation-standard.md)

## Lifecycle

Detections should use one of the following lifecycle values:
- experimental
- testing
- production
- deprecated

See:
- [Lifecycle Standard](../governance/lifecycle-standard.md)
- [Detection Lifecycle](../docs/02_process/detection-lifecycle.md)

## Related Content

- [Triage Guides](../content/triage-guides/)
- [Detection Tracking Matrix](../docs/04_reporting/detection_tracking_matrix.csv)
- [Coverage](../coverage/)
- [Governance](../governance/)

## Goal

The goal of this directory is to manage detection content as structured, governed, and maintainable engineering artifacts.