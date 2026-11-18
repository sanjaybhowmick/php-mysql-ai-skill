# Security Guidance

This skill is a development aid. It does not automatically make generated code secure.

## Minimum review areas

- Authentication and authorisation.
- SQL injection.
- XSS and context-specific output encoding.
- CSRF.
- Session fixation and cookie configuration.
- Broken access control and IDOR.
- File upload and download handling.
- Secrets management.
- Error and log exposure.
- Dependency vulnerabilities.
- Rate limiting for sensitive actions.
- Backup, restore, and deployment permissions.

## SQL

Prepared statements are generally the safer choice for values. If a project explicitly uses escaped traditional MySQLi queries, use the same active connection for escaping, validate/cast values, allowlist identifiers, and review every dynamic query. Escaping does not protect SQL identifiers and is not equivalent to parameterisation.

## Uploads

Do not trust filename, extension, or browser MIME type. Inspect actual file content, restrict allowed types, use random names, prevent execution, store private files outside the public root where possible, and enforce access checks on downloads. MIME inspection is not a guarantee that a file is harmless.

## Secrets

Do not commit credentials, tokens, private keys, or production configuration. Use environment variables or protected configuration. Rotate exposed secrets.

## Testing

Test negative cases and access boundaries, not only successful workflows. Do not claim security certification based on a checklist. Obtain specialist review for high-risk applications.
