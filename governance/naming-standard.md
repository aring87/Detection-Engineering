# Naming Standard

## Purpose

This standard defines naming expectations for files, identifiers, folders, and related content artifacts in the detection engineering repository.

Consistent naming improves clarity, usability, automation readiness, and long-term maintainability.

---

## Objectives

This standard is intended to:

- create predictable repository structure
- improve readability and consistency
- reduce ambiguity in content identification
- support quality checks and future automation
- make reporting and maintenance easier

---

## General Naming Principles

Names should be:

- clear
- concise
- descriptive
- consistent
- easy to sort and search
- aligned to repository structure

Avoid names that are:
- vague
- overly long
- inconsistent in case or separators
- difficult to distinguish from similar content

---

## File Naming Standard

Detection files should use:
- lowercase letters
- hyphens as separators
- descriptive names tied to the behavior

### Example
`powershell-encoded-command-execution.yml`

### Avoid
- mixed case without reason
- spaces in filenames
- overly generic names like `rule1.yml`
- inconsistent punctuation

---

## Folder Naming Standard

Folders should use:
- lowercase letters
- hyphens where needed
- tactic or content names that are easy to understand

### Example
- `reconnaissance`
- `resource-development`
- `initial-access`
- `privilege-escalation`

### Goal
Keep repository paths clean, readable, and consistent across content types.

---

## Detection ID Standard

Detection IDs should be:
- unique
- stable over time
- aligned to platform or content family where appropriate

### Recommended Format
`SENT-TACTIC-####`

### Examples
- `SENT-EXEC-0001`
- `SENT-CRED-0004`
- `SENT-DISC-0012`

### Notes
- platform prefix helps distinguish content families
- tactic code improves readability
- numeric suffix supports scalability

---

## Suggested Tactic Code Examples

Examples may include:
- `RECON`
- `RESDEV`
- `INIT`
- `EXEC`
- `PERSIST`
- `PRIV`
- `DEFEV`
- `CRED`
- `DISC`
- `LATERAL`
- `COLL`
- `C2`
- `EXFIL`
- `IMPACT`

Choose one consistent internal style and use it uniformly.

---

## Document Naming Standard

Documents should use:
- lowercase letters
- hyphens
- descriptive names tied to purpose

### Examples
- `program-charter.md`
- `metrics-catalog.md`
- `exception-management.md`

---

## Visual Naming Standard

Visual files should use:
- lowercase letters
- hyphens
- names that describe the content clearly

### Examples
- `detection-content-lifecycle.png`
- `detection-engineering-operating-model.svg`

---

## Naming Change Guidance

Renaming should be:
- deliberate
- documented through git history
- kept minimal once a stable naming convention is in place

Frequent renaming without purpose creates unnecessary churn.

---

## Naming Quality Questions

Before naming a file or document, ask:
- is it clear what this artifact is?
- is the name consistent with similar artifacts?
- will this sort and search well later?
- does it align with repository conventions?

---

## Summary

A strong naming standard helps make the repository readable, governable, and automation-friendly by ensuring files, folders, IDs, and documents follow a clear and consistent pattern.