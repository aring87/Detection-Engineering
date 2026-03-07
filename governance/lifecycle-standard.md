# Lifecycle Standard

## Purpose

This standard defines the allowed lifecycle states for detection content and the expectations associated with each state.

The purpose is to ensure lifecycle values are used consistently and accurately across the repository.

---

## Objectives

This standard is intended to:

- create a shared meaning for lifecycle states
- improve visibility into detection maturity
- support structured promotion and retirement
- reduce misuse of maturity labels
- improve reporting and governance consistency

---

## Allowed Lifecycle States

The standard lifecycle states are:

- experimental
- testing
- production
- deprecated

No additional lifecycle states should be introduced unless the governance model is formally updated.

---

## Lifecycle Definitions

## Experimental

### Description
Content in the experimental state is early-stage and not yet considered mature for normal operational reliance.

### Typical Characteristics
- initial logic has been created
- metadata exists in basic form
- ATT&CK mapping is present or drafted
- documentation may still be developing
- quality may still vary
- the rule is not yet considered fully ready

### Use Case
Experimental is appropriate for:
- newly authored detections
- early repository imports
- draft use case coverage
- content still being shaped into program standards

---

## Testing

### Description
Content in the testing state is more developed and is being actively assessed for broader operational readiness.

### Typical Characteristics
- metadata is more complete
- structure aligns more closely to standards
- documentation is improving
- validation notes may exist
- lifecycle and severity are being treated more deliberately
- the rule is under active refinement

### Use Case
Testing is appropriate for:
- detections under active review
- rules being prepared for production consideration
- content with improving documentation and operational context

---

## Production

### Description
Content in the production state is considered sufficiently mature for normal operational use within the program.

### Typical Characteristics
- required metadata is complete
- lifecycle and severity are intentional
- ownership is clear
- documentation is usable
- the rule is maintainable and governed
- the rule is treated as active program content

### Use Case
Production is appropriate for:
- detections with strong documentation and governance
- rules intended for normal analyst or engineering reliance
- content that is actively maintained as a mature program asset

---

## Deprecated

### Description
Content in the deprecated state is no longer recommended for active use.

### Typical Characteristics
- the detection is obsolete, replaced, duplicated, or no longer aligned to program needs
- the content is preserved for historical traceability
- the lifecycle clearly signals that the rule is no longer active program content

### Use Case
Deprecated is appropriate for:
- replaced detections
- duplicate or outdated logic
- content retained for recordkeeping but not active use

---

## Lifecycle Assignment Guidance

Lifecycle values should reflect actual maturity, not aspiration.

Questions to ask:
- is the rule structured but still early?
- is it under active review and becoming more usable?
- is it governed and mature enough to represent stable content?
- should it no longer be treated as active?

---

## Lifecycle Promotion Expectations

Promotion from one lifecycle state to another should consider:
- metadata completeness
- documentation quality
- logical coherence
- mapping quality
- ownership clarity
- review confidence
- operational readiness

Promotion should be deliberate and visible in repository history.

---

## Lifecycle Misuse to Avoid

Avoid:
- labeling unfinished content as production
- leaving imported content indefinitely unclassified
- using testing as a permanent placeholder with no review
- failing to mark obsolete detections as deprecated

---

## Reporting Value

Lifecycle states support:
- maturity reporting
- tracking matrix updates
- quarterly review content
- roadmap progress visibility
- portfolio health assessment

---

## Summary

Lifecycle states are a governance tool. They help communicate maturity, support reporting, and ensure detection content is managed as a structured program asset rather than a static collection of files.