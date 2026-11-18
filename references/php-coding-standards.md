# PHP Coding Standards

## General

- Target the PHP version declared in the project. For new projects, use the PHP 8.x default and version-selection policy in `technology-versions.md`. Avoid deprecated functions and syntax, and do not use syntax newer than the project runtime supports.
- Use procedural PHP by default.
- Use clear, descriptive variable and function names.
- Use `snake_case` for functions and variables unless an existing project convention differs.
- Use `__DIR__` for reliable include paths.
- Use `require_once` for essential shared dependencies.
- Omit the closing `?>` tag in PHP-only files.
- Keep configuration, business logic, database operations, and presentation reasonably separated.
- Avoid excessive globals and duplicated code.

## File organisation

Use small, purpose-specific files. Keep shared functions in common includes and business functionality in modules. Do not create one large PHP file for an entire application.

## Input validation and output encoding

Validate input against expected types, lengths, ranges, formats, and allowed values. Reject invalid values rather than trying to make arbitrary input safe.

Use context-appropriate output encoding. For HTML text and quoted attributes:

```php
function e($value): string
{
    return htmlspecialchars(
        (string) $value,
        ENT_QUOTES | ENT_SUBSTITUTE,
        'UTF-8'
    );
}
```

This helper is for HTML contexts only. JavaScript, CSS, URL, and JSON contexts require their own safe handling. Do not HTML-encode data before storing it in the database.

## Database access

Use the central MySQLi connection and `utf8mb4`. Follow `database-standards.md` for the project's selected query policy. Never concatenate untrusted values directly into SQL.

## Forms

- Use POST for state-changing operations.
- Validate on the server.
- Include and verify CSRF tokens.
- Preserve safe submitted values after validation errors.
- Use Post/Redirect/Get after successful form submissions where appropriate.
- Do not rely on HTML `required`, JavaScript, or disabled controls for security.

## Sessions and authentication

Configure session cookies securely before starting the session. Regenerate the session ID after authentication and privilege changes. Use `password_hash()` and `password_verify()`. Do not store plaintext passwords or reusable reset tokens.

## Errors and logging

Show users generic, helpful messages. Log technical details privately. Do not display stack traces, SQL statements, credentials, filesystem paths, or SMTP details in production.

## Time

Set the application timezone before generating timestamps. Use PHP-generated application-local timestamps according to the project's storage strategy.

## Code delivery

When changing an existing file, inspect its complete relevant logic and dependencies. Preserve unrelated functionality. Identify filenames, SQL changes, configuration, and manual steps.
