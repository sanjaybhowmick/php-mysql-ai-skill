# Example Prompts for AI Coding Agents

Use these prompts as starting points. Replace placeholders with your actual project details.

## Load the skill

Read `SKILL.md` and the relevant references in `custom-php-mysql-development`. Summarise the applicable coding, SQL, security, pagination, timezone, and UI rules. Do not modify files yet.

## Inspect an existing project

Inspect this PHP project before changing anything. Review the folder structure, database connection, schema, authentication, permissions, shared functions, and relevant modules. Report the architecture and risks. Do not modify files yet.

## Analyse a new requirement

Analyse this requirement: [PASTE REQUIREMENT]. Identify actors, workflows, fields, validation, permissions, database entities, reports, integrations, and ambiguities. Ask only essential clarification questions. Do not code yet.

## Plan a module

Prepare a phased implementation plan for [MODULE]. Include SQL changes, backend pages, permissions, server-side pagination, validation, security, testing, and documentation. Reuse the existing architecture.

## Implement a module

Implement [MODULE] according to the approved plan. Inspect existing code first. Make focused changes, preserve unrelated functionality, include required SQL migrations, validate all input server-side, enforce permissions, and use server-side pagination.

## Review security

Review the changed files for SQL injection, XSS, CSRF, broken access control, IDOR, unsafe uploads, session issues, secrets exposure, and unsafe error handling. Report findings by severity and fix only after explaining any material behaviour changes.

## Test and report

Test the changed functionality where the environment permits. Report exactly which tests were run, which were not run, files changed, SQL changes, manual steps, and pending issues. Do not claim unperformed tests passed.
