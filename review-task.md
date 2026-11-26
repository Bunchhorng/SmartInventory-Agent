# Antigravity — independent review of Phase 6.1

Read shared rules, actual diff, relevant architecture, migrations, services, routes, tests and Codex handoff. Review only; do not modify production files, auto-fix, or start another phase unless explicitly authorized.

## Review checklist
- Existing shared ledger and cost service reused; no parallel inventory truth.
- Paired movements, valid source/destination, conversion snapshots, aggregated availability, quarantine restriction, no negative stock.
- Atomic transactions, deterministic locks compatible with other stock writers, idempotency, immutable confirmed documents, exact conservation of quantity/value/average and zero financial effects.
- Real route authorization, CSRF, HTTP method restrictions, input validation, no mass assignment or Staff cost leakage; audit consistency and sensitive error handling.
- Forward-only migration, foreign keys/unique constraints/indexes as appropriate, fresh schema compatibility, no unsafe main DB import, no credentials or public backups.
- Test evidence: actual concurrent independent connections, post-write fault injection and retry, previous regression suites, reconciliation, syntax, clean disposable DB; distinguish CLI route tests from external HTTP tests.

## Review output
List findings in severity order (Critical, High, Medium, Low) with actual file/line evidence, impact, reproduction where safe, and proposed fix. Separate observed defects from assumptions and untested risks. Report commands actually executed. If running tests, use only explicitly disposable schemas with safety checks. Never claim PASS if required evidence is missing. Final verdict: APPROVE, CHANGES REQUIRED, or BLOCKED. Owner decides closure; Codex implements any approved fixes.
