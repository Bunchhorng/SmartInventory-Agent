# SmartStock

A private inventory, purchasing, sales and business decision-support system for a single owner and physical business location with multiple internal storage locations. Owner and authorized staff use the system; no public registration. The eventual goal is secure mobile access to business data from anywhere.

## Technology
PHP 8.2+ (target 8.3), custom MVC, PDO, MySQL InnoDB, Bootstrap, jQuery/AJAX. Local development with Laragon. Preserve current project setup rather than introducing new frameworks.

## Business scope
Retail and wholesale sales; product-specific unit conversions; inventory locations; purchasing and supplier payables; customer receivables; KHR/USD payments and manual bank/KHQR verification; returns and compensating corrections; expenses and profit reporting; fuel operations; future stock reorder suggestions.

## Getting started
Read the existing local setup guide and configuration templates. Set up a private local environment using the actual repository conventions. Confirm MySQL is running. Never commit credentials. Do not import or run migrations against the main `smartstock` database without explicit owner authorization and verified backup. Use `smartstock_test` for destructive tests. Exact setup and test commands must be derived from the local repository, not guessed.

## Agent coordination
- AGENTS.md: shared rules
- TASKS.md: phase status and assignments
- architecture.md: technical and business design
- backend-task.md: Codex assignment
- frontend-task.md: Gemini assignment
- review-task.md: Antigravity assignment

## Current milestone
Phase 5.8 is reported PASS; Phase 6.1 internal stock transfers is the next known assignment, subject to local inspection. The main database has not been migrated through the newer phases. The project is not declared production-ready. Preserve existing README sections and setup instructions when merging this overview.
