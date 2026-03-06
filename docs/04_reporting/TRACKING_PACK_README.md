# Detection Engineering Tracking Pack

This pack contains:
- `detection_tracking_matrix.csv` — tracker for all starter Sentinel rules
- `content/triage-guides/priority-starter-rules/` — triage guides for the highest-priority starter detections

## Suggested use
1. Copy `detection_tracking_matrix.csv` into the repo root or `docs/04_reporting/`.
2. Copy the triage guide markdown files into `content/triage-guides/priority-starter-rules/`.
3. For each rule, update:
   - validation_status
   - tuning_status
   - production_readiness
   - notes
4. Move rules from `experimental` to `testing` only after:
   - field names are validated
   - false positives are documented
   - triage steps are usable
   - test evidence exists
