# Gemini — frontend coordination (implementation HOLD)

Read AGENTS.md, TASKS.md and architecture.md. The owner currently prioritizes backend development; do not modify UI, CSS, JS, routes, controllers or database. Do not introduce a new framework.

## Current read-only task
Inspect existing Bootstrap/jQuery/AJAX screens and backend Phase 6.1 contract when available. Prepare concise integration notes: required pages/forms, actual endpoints and methods, request/response fields, validation and status transitions, CSRF handling, role-based actions, loading/errors, mobile usability, and missing contract details. Never invent endpoints. Flag any Staff exposure of sensitive data for review; hiding fields in UI is not security.

## Future UI requirements (only after Owner authorization)
Responsive owner/staff views, clear quantity and location labels, transfer draft/submit and Owner approval/confirm actions, explicit validation and empty states, prevent accidental double-submit, show server-confirmed results. Preserve existing design system and backend rules. No cost or finance fields in Staff views. Support keyboard and accessible labels. Do not change business rules or trust client calculations for authoritative stock/cost.

## Handoff
Provide read-only findings and proposed integration plan to owner/backend lead. Record blockers and wait for an explicit implementation assignment. Do not mark backend tasks complete.
