# SmartStock — shared agent rules

## Mission
Build a reliable inventory and sales system for one owner, one physical business, and multiple internal stock locations. Support groceries, agricultural goods, animal feed, veterinary goods and fuel. Help the owner decide what to buy, how much, and when. Remote mobile access is a future deployment goal, not the current development task.

## Stack and boundaries
PHP 8.2+ (target 8.3), custom OOP MVC, PDO, MySQL InnoDB, Bootstrap, jQuery/AJAX. Local root: `C:\laragon\www\SmartInventory\SmartStock`. MySQL test environment reported as 8.4.3 at 127.0.0.1:3306. Preserve existing conventions; no framework rewrite, Laravel, React, Docker, Redis or new infrastructure without owner approval. Do not assume cron or shell access on hosting.

## Every agent must
1. Read this file, TASKS.md, architecture.md, its role file, relevant phase documentation and actual code before changes. Existing implementation is evidence; these files are coordination instructions, not proof of schema or test results.
2. Inspect git status and existing changes. Never overwrite another agent's work, revert user changes, or commit/push without authorization. Coordinate shared files and report conflicts.
3. Work on the assigned scope only; no UI redesign during backend milestones. Keep changes small and backward compatible.
4. Use forward-only migrations, prepared statements, server-side validation, RBAC, CSRF and audit events. Owner creates staff accounts; no public registration. Preserve forced password changes and session revocation. Never expose costs, profit, supplier finance or valuation to Staff through any response, export or error.
5. Use immutable posted documents and compensating entries. Use transactions, deterministic locks, unique posting references, idempotency and fixed-point decimal arithmetic. Preserve current shared stock and valuation services; never build parallel ledgers. Never silently repair reconciliation differences.
6. Do not modify or migrate the main `smartstock` DB. Destructive tests only on `smartstock_test` or explicitly disposable smoke DBs. Assert active schema before every import/test; reject or sanitize embedded database-selection directives and unsafe qualified references; use a restricted test DB account where possible. Never access production data for tests. Back up and obtain explicit owner approval before any future main migration.
7. Run actual tests, report exact commands/results and failures; never label a phase PASS based only on syntax. Include concurrency, rollback, route RBAC/CSRF, privacy, reconciliation and regression checks as applicable. Clean test fixtures and smoke DBs.
8. Do not store secrets, credentials or backups in git/public directories. Do not add production-accessible test hooks.
9. Update TASKS.md and the relevant phase handoff only with observed results. Preserve existing documentation; merge rather than blindly replace. Review is required before marking a milestone closed. No next phase until authorized.

## Roles
- Codex: backend lead; migrations, services, models, controllers, tests; current assignment Phase 6.1.
- Gemini: frontend lead; currently HOLD for UI implementation; may read contracts and prepare integration notes only.
- Antigravity: independent reviewer; inspect correctness, security, database safety and test coverage; no automatic fixes or feature implementation.
- Owner: approves business rules, changes to scope, phase closure and production deployment.

## Handoff format
Phase / status; files changed; migration order; business rules; commands and actual results; security, concurrency and rollback evidence; database cleanup; main DB preservation; limitations; proposed next task. State unverified claims explicitly.




# AI Development Team Rules

## Team Roles

- Codex: Backend developer.
- Gemini: Frontend developer.
- Antigravity: QA engineer and code reviewer.
- Human: Team leader and final decision maker.

## Rules

1. Read this file before starting work.
2. Read README.md and architecture documentation.
3. Read TASKS.md before working.
4. Only work on your assigned task.
5. Do not modify another agent's assigned files.
6. Do not overwrite another agent's work.
7. Use Git for version control.
8. Report completed tasks.
9. Report problems instead of hiding them.
10. Do not delete files without approval.

## Communication

- Use task files to share instructions.
- Use Git commits to share changes.
- Use review reports to share feedback.
- The human leader approves major decisions.
