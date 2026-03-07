# Severity Standard

## Purpose

This standard defines how severity should be assigned to detection content in the repository.

The goal is to improve consistency in how detections communicate potential importance and expected analyst attention.

---

## Objectives

This standard is intended to:

- create a common meaning for severity values
- reduce inconsistent severity assignment
- support triage and reporting
- align severity with detection intent and likely risk
- improve governance and program clarity

---

## Standard Severity Levels

The recommended severity levels are:

- low
- medium
- high
- critical

These values should be used consistently unless a formal governance change introduces a different model.

---

## Severity Definitions

## Low

### Description
The detection may indicate low-confidence or low-impact suspicious behavior, or an activity that is important for visibility but not immediately severe on its own.

### Typical Use Cases
- broad awareness detections
- supporting signals
- low-risk suspicious activity
- early-stage behaviors that need additional context

---

## Medium

### Description
The detection indicates behavior that is suspicious and operationally useful, but which may still require contextual review before being treated as highly urgent.

### Typical Use Cases
- behavior that is often suspicious but may have benign overlap
- detections intended to support meaningful triage
- content that may indicate attacker activity depending on context

---

## High

### Description
The detection indicates behavior strongly associated with malicious activity, important attacker tradecraft, or meaningful security impact.

### Typical Use Cases
- common adversary execution patterns
- persistence behaviors
- credential access indicators
- destructive or clearly abnormal actions
- detections expected to carry strong investigative value

---

## Critical

### Description
The detection indicates behavior associated with severe security impact, high-confidence malicious activity, or a condition that demands immediate attention.

### Typical Use Cases
- ransomware-style impact behaviors
- high-confidence credential theft
- major privileged abuse
- severe exfiltration or destructive events
- detections whose operational meaning is highly urgent

---

## Severity Assignment Guidance

Severity should reflect:
- the behavior being detected
- likely security impact
- confidence implied by the logic
- need for urgent attention
- expected overlap with benign activity
- operational consequences if the activity is real

Severity should not be assigned based only on how interesting a rule feels.

---

## Severity Questions

Before assigning severity, ask:
- how dangerous is this behavior if true?
- how much benign overlap is expected?
- how quickly would an analyst need to care?
- does the rule indicate direct malicious action or only supporting context?
- is this a high-confidence signal or an early suspicious pattern?

---

## Severity vs Lifecycle

Severity and lifecycle are not the same thing.

Examples:
- a high-severity rule can still be experimental
- a production rule can still be medium severity
- critical severity should not automatically be assigned just because a rule is important strategically

Lifecycle describes maturity.  
Severity describes expected importance.

---

## Severity Review Expectations

Severity should be reviewed when:
- logic changes significantly
- false-positive expectations shift
- the use case becomes better understood
- the rule moves toward a more mature lifecycle state

---

## Reporting Value

Severity supports:
- triage expectations
- metrics and reporting
- prioritization views
- portfolio analysis by risk and content type

---

## Summary

Severity should be assigned intentionally and consistently so detections communicate meaningful operational importance without overstating confidence or urgency.