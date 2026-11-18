# CRUD Development Standards

## Module planning

Before building CRUD functionality, identify fields, data types, business rules, relationships, duplicate rules, permissions, and audit requirements. Inspect existing tables and reusable functions first.

## Typical pages

A module may contain:
- `list.php`
- `add.php`
- `edit.php`
- `view.php`
- action handlers for delete, status changes, or other operations

Keep Add and Edit separate by default unless the project has a clear reason to combine them.

## Listing

Every database listing must use server-side pagination. Search, filters, and sorting must execute server-side. Validate page and page-size values. Allowlist sort columns and direction. Do not use jQuery DataTables or load the full dataset into the browser.

## Create and update

Validate every field on the server. Check required values, types, lengths, allowed values, ranges, relationships, and duplicates. Use CSRF protection. Check authentication and permission before processing. Preserve safe values after validation errors.

## Delete and status changes

Prefer deactivation or soft deletion when records are referenced by financial, audit, or business history. Use hard deletion only when business rules permit it. Confirm destructive actions and enforce permissions on the server.

## SQL

Use the project's selected MySQLi query policy. Prepared statements are the safer general recommendation. If using escaped traditional queries, validate and cast values, escape strings with the active connection, and allowlist identifiers. Never concatenate untrusted values.

## Audit

Record important create, update, delete, and status changes where required. Do not log secrets. Use application timestamps.

## Completion checks

Test valid and invalid inputs, duplicate handling, permissions, CSRF, pagination, search, filters, sorting, empty states, and related-record integrity.
