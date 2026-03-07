# Analytic Quality Standard

## Purpose

This standard defines the minimum quality expectations for detection content managed within the detection engineering repository.

The goal is to ensure that detections are understandable, governed, maintainable, and useful as engineering artifacts rather than just isolated alert logic.

---

## Objectives

This standard is intended to:

- improve consistency across detection content
- establish a baseline for analytic quality
- support lifecycle progression
- improve review clarity
- strengthen documentation and reporting
- reduce unmanaged or low-context content growth

---

## Quality Principles

Analytic content should be:

### Clear
The intent of the detection should be understandable from its title, description, metadata, and structure.

### Consistent
Detections should follow repository standards for schema, naming, severity, lifecycle, and placement.

### Traceable
Changes should be visible through version control, comments, and supporting program artifacts.

### Maintainable
Detections should be structured so future updates are manageable and understandable.

### Explainable
A reviewer or analyst should be able to understand what the detection is trying to identify and why it matters.

### Governed
Detections should align to lifecycle, severity, tagging, and quality expectations defined in the repository.

---

## Minimum Analytic Quality Expectations

Every detection should meet the following baseline expectations.

## 1. Clear Purpose

A detection should clearly state:
- what behavior it is meant to identify
- why the behavior matters
- what platform or telemetry it applies to

### Goal
Ensure the rule has a defined purpose and is not just a technical pattern without context.

---

## 2. Required Metadata

A detection should include expected metadata such as:
- title
- unique identifier
- description
- author
- date and/or modified date
- platform
- severity
- lifecycle
- tactics and techniques
- data sources
- tags
- owner where applicable

### Goal
Ensure the rule is governable, reportable, and trackable.

---

## 3. Logical Coherence

The logic should align with the stated purpose of the detection.

Questions to ask:
- does the query reflect the described behavior?
- is the mapping consistent with the logic?
- are severity and lifecycle reasonable?
- is the rule understandable to a reviewer?

### Goal
Ensure the analytic is internally consistent.

---

## 4. Reasonable Mapping

Mappings should be:
- relevant
- not overly broad
- useful for reporting
- aligned with the described behavior

### Goal
Ensure ATT&CK and CKC reporting remains meaningful.

---

## 5. Documentation Support

Where possible, detections should include:
- false-positive considerations
- triage guidance
- validation notes
- ownership visibility

### Goal
Ensure detections are usable beyond raw query logic alone.

---

## 6. Structural Consistency

A detection should:
- follow the standard schema
- be stored in the correct repository location
- use correct naming conventions
- use the correct lifecycle state

### Goal
Ensure the repository remains predictable and scalable.

---

## 7. Operational Readiness Alignment

A detection’s metadata and documentation should reflect its actual maturity.

Examples:
- experimental detections may be early but should still be structured
- production detections should not be missing key governance fields
- deprecated detections should be clearly marked and understandable

### Goal
Ensure lifecycle labels are meaningful.

---

## Quality Review Questions

Reviewers should be able to answer:
- what does this detection do?
- why does it exist?
- does the logic match the use case?
- is the metadata complete?
- is the mapping reasonable?
- is the lifecycle assignment appropriate?
- is the rule maintainable?

---

## Quality Outcomes

A detection may be considered:

### Acceptable
Meets baseline expectations for its lifecycle stage.

### Needs Improvement
Useful content exists, but metadata, documentation, or structure should be improved.

### Rework Required
The detection has significant issues in logic, structure, or clarity.

### Deprecated Candidate
The content may no longer be appropriate or useful in its current state.

---

## Program Alignment

This quality standard is supported by:
- QA and validation standard
- change control
- lifecycle standard
- naming standard
- severity standard
- tagging standard
- tracking matrix
- contribution workflow

---

## Summary

Analytic quality is not just about whether a query exists. It is about whether the detection is clear, governed, documented, and maintainable enough to function as part of a mature detection engineering program.