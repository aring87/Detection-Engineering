# Triage Guides

This directory contains analyst-facing triage guides that support the operational use of detections in the repository.

## Purpose

Triage guides help SOC analysts and incident responders understand:
- what a detection is intended to identify
- why it matters
- what questions to ask first
- what evidence to review
- when to escalate
- what common benign explanations may exist

The goal is to make detections more actionable and easier to investigate consistently.

## Structure

### Priority Starter Rules
- [Priority Starter Rules](priority-starter-rules/)

These guides support the highest-priority starter detections currently included in the repository.

## What a Triage Guide Should Include

A strong triage guide should usually contain:
- detection title
- objective
- alert logic summary
- initial triage questions
- investigation steps
- common false positives
- escalation guidance
- recommended enrichment sources

## Intended Audience

These guides are primarily intended for:
- SOC analysts
- incident responders
- detection engineers reviewing analyst usability
- threat hunters who need quick operational context

## Relationship to Detection Engineering

Triage guides are an important part of detection maturity. A detection is more operationally useful when analysts can quickly understand:
- what it means
- how to investigate it
- when it is likely benign
- when it should be escalated

## Related Content

- [Detection Rule Template](../templates/detection-rule-template.yml)
- [Triage Guide Template](../templates/triage-guide-template.md)
- [Detection Tracking Matrix](../../docs/04_reporting/detection_tracking_matrix.csv)
- [Detection Lifecycle](../../docs/02_process/detection-lifecycle.md)

## Goal

The goal of this directory is to improve analyst usability, investigation consistency, and the overall operational readiness of detection content.
