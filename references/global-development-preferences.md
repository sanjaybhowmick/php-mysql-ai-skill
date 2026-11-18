# Global Development Preferences

These are defaults for projects using this skill. A project's explicit requirements may override them.

## Technology and architecture

- PHP 8.x, MySQL, MySQLi.
- Procedural PHP by default; avoid introducing a framework or object-oriented architecture without a reason.
- Bootstrap 5 for the interface.
- jQuery is acceptable for non-tabular interactions.
- Font Awesome and PHPMailer may be used where appropriate.
- Prefer local, version-pinned assets over CDN dependencies.
- Keep third-party dependencies minimal and document their versions and licences.

## SQL and security

The skill maintainer prefers traditional MySQLi queries with rigorous escaping. This is a project preference, not a claim that escaped concatenation is as safe as prepared statements.

For escaped-query projects:
1. Set the connection charset to `utf8mb4`.
2. Validate input according to its expected type and business rules.
3. Cast integer values and validate numeric ranges.
4. Escape every dynamic string with the same active MySQLi connection.
5. Allowlist dynamic identifiers and sort directions.
6. Never interpolate untrusted values directly.

Prepared statements are the safer general recommendation for public users and should be used when the project has no established query-style preference, or when query complexity/sensitivity makes escaping error-prone.

Always use server-side validation, output-context encoding, CSRF protection, authentication and permission checks.

## Tables and performance

- Every database listing uses server-side pagination.
- Search, filters, and sorting are performed server-side.
- Do not use jQuery DataTables.
- Do not load large result sets into the browser.
- Add indexes based on actual filters, joins, and sort patterns.
- Review N+1 queries, repeated queries in loops, and expensive joins.
- Consider cursor pagination for very large datasets where OFFSET becomes inefficient.

## User interface

- Use Bootstrap 5 unless the project specifies otherwise.
- Keep the interface minimal, clean, professional, responsive, and consistent.
- No gradients, flashy AI-style buttons, excessive shadows, or unnecessary animation.
- Use centrally managed branding and CSS variables.
- Typography must suit the content and available space. Keep tables readable; use horizontal scrolling rather than shrinking text excessively.
- Prefer system fonts or locally hosted fonts.

## Validation and security

Every form requires server-side validation. Client-side validation is an additional usability feature only.

Review each module for SQL injection, XSS, CSRF, broken access control, insecure direct object references, session weaknesses, file upload risks, sensitive-data exposure, and unsafe error handling.

Never trust hidden fields, client-side checks, filenames, MIME headers, or user-supplied paths.

## Timezone and timestamps

Default timezone: `Asia/Kolkata`.

Set the configured timezone in PHP before generating application timestamps. Use PHP-generated values such as:

```php
date_default_timezone_set(APP_TIMEZONE);
$current_datetime = date('Y-m-d H:i:s');
```

Do not rely on MySQL `NOW()` or `CURRENT_TIMESTAMP` for application-local timestamps when PHP-controlled local time is required. For multi-timezone applications, explicitly define whether timestamps are stored in UTC and converted for display.

## Configuration and dependencies

Centralise technical configuration and administrator-managed application settings separately. Do not expose credentials through the settings interface.

Prefer local assets. Pin versions, document dependencies, review licences, and keep security updates current.
