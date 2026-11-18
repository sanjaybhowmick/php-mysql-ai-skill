# Database Standards

## Naming and schema

- Use lowercase `snake_case`.
- Prefer descriptive table and column names.
- Use InnoDB and `utf8mb4`.
- Use primary keys and appropriate foreign keys.
- Use `DECIMAL` for money; never floating-point types for exact financial values.
- Choose data types and lengths based on actual requirements.
- Add indexes for frequently used filters, joins, and ordering.
- Avoid indexing every column without justification.
- Use `created_at`, `updated_at`, `created_by`, and `updated_by` where useful.
- Use transactions for multi-step operations that must succeed or fail together.

## Query security policy

MySQLi is the default database interface.

**General recommendation:** Use MySQLi prepared statements for new applications. They separate SQL syntax from values and reduce the risk of injection.

**Maintainer preference profile:** Where the project explicitly follows traditional MySQLi query execution, escaped values may be used only with strict discipline:
- Set `$conn->set_charset('utf8mb4')` after connecting.
- Validate input types and business rules before building SQL.
- Cast validated integers.
- Escape every dynamic string using `$conn->real_escape_string($value)` on the same connection.
- Allowlist identifiers, column names, and sort directions; escaping does not make identifiers safe.
- Never interpolate raw request values.
- Review dynamic `IN` clauses and complex conditions carefully; prefer prepared statements when escaping becomes difficult.

Escaping is not equivalent to prepared statements. Do not describe it as equally safe.

## Identifiers and sorting

Never accept a table name, column name, SQL fragment, or sort direction directly from a request. Map user-facing sort choices to a fixed allowlist. Validate direction as `ASC` or `DESC`.

## Pagination

Use server-side pagination for all database listings. Validate page numbers and page sizes. Count records using an appropriate query and fetch only the requested page. Use indexed sort columns. For very large datasets, assess keyset/cursor pagination instead of large OFFSET values.

## Timestamps

When application-local time is required, generate timestamps in PHP after setting the configured timezone and explicitly supply them in INSERT/UPDATE statements. Avoid relying on database `NOW()` or `CURRENT_TIMESTAMP` for these values. For multi-timezone applications, document whether UTC is stored and converted for display.

## Integrity and migrations

Use foreign keys where appropriate. Handle related writes in transactions. Provide forward migration scripts and practical rollback guidance. Never run destructive schema changes without checking existing data and obtaining appropriate approval.

## Performance

Avoid `SELECT *` when only a subset is needed. Avoid queries inside loops when a join or batch query is suitable. Inspect query plans for slow queries. Add indexes based on measured or expected access patterns. Do not retrieve all rows merely to paginate them in PHP.
