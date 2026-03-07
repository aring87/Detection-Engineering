# Tagging Standard

## Purpose

This standard defines how tags should be used in the detection engineering repository.

The goal is to ensure tags provide consistent value for organization, filtering, reporting, and future automation rather than becoming inconsistent free-form labels.

---

## Objectives

This standard is intended to:

- improve searchability and filtering
- support ATT&CK and coverage reporting
- improve repository consistency
- support future automation and content quality checks
- reduce inconsistent or low-value tagging practices

---

## Tagging Principles

Tags should be:

- consistent
- meaningful
- reusable
- easy to interpret
- aligned to repository goals
- limited to useful categories

Tags should not become a dumping ground for arbitrary labels.

---

## Recommended Tag Categories

The repository should primarily use tags in the following categories:

### 1. ATT&CK Tags
Used to represent ATT&CK tactic or technique alignment.

### 2. Kill Chain Tags
Used to represent Cyber Kill Chain alignment where applicable.

### 3. Platform Tags
Used to identify the detection platform or content family.

### 4. Behavior or Tooling Tags
Used to describe important recurring behavioral themes such as:
- powershell
- mshta
- registry
- scheduled-task
- dns
- lsass

These should be used carefully and consistently.

---

## ATT&CK Tag Format

Recommended format:
- `attack.execution`
- `attack.persistence`
- `attack.t1059.001`

### Guidance
- use tactic tags where appropriate
- use technique tags when the mapping is clear
- avoid adding incorrect or speculative ATT&CK tags

---

## Cyber Kill Chain Tag Format

Recommended format:
- `ckc.reconnaissance`
- `ckc.weaponization`
- `ckc.delivery`
- `ckc.exploitation`
- `ckc.installation`
- `ckc.command-and-control`
- `ckc.actions-on-objectives`

### Guidance
Use only the phases that clearly fit the rule’s behavior.

---

## Platform Tag Format

Recommended examples:
- `sentinel`
- `splunk`
- `sigma`

### Guidance
Use platform tags consistently so content families can be filtered easily.

---

## Behavior Tag Format

Behavior tags should be:
- short
- descriptive
- reused consistently

### Examples
- `powershell`
- `encoded-command`
- `run-key`
- `service-creation`
- `dns-tunneling`
- `lsass`
- `wmi`

Avoid redundant or overly vague tags such as:
- `suspicious`
- `investigate`
- `important`

---

## Tagging Rules

### Use Tags Deliberately
Only add tags that provide filtering or reporting value.

### Avoid Tag Explosion
Do not create too many custom tags that are used only once.

### Keep Formatting Consistent
Use lowercase and hyphenated or dotted formats consistently.

### Align to Mappings
Tags should support, not contradict, tactic and technique fields.

---

## Recommended Minimum Tags for Detections

At a minimum, detections should usually include:
- relevant ATT&CK tactic tag
- ATT&CK technique tag if appropriate
- platform tag
- one or more meaningful behavior tags where useful

---

## Review Questions

Before adding a tag, ask:
- does this tag help someone find or classify the rule?
- is this tag already used elsewhere?
- is the formatting consistent?
- does the tag reflect actual behavior or mapping?

---

## Summary

A strong tagging standard improves the usefulness of the repository by making detections easier to search, filter, report on, and manage while avoiding inconsistent or low-value labels.