# Authentication and User Permissions

## Core requirements

Implement authentication and authorisation on the server. Hiding a link or button is not access control. Every protected page, action, and AJAX endpoint must independently verify access.

## Suggested data model

Typical tables include:
- `users`
- `roles`
- `permissions`
- `user_roles`
- `role_permissions`

Adapt the schema to the project's needs. Enforce unique constraints and indexes where appropriate.

## Passwords

Use `password_hash()` and `password_verify()`. Never store plaintext passwords or reversible password encryption. Use secure, single-use, time-limited password-reset tokens. Store only a hash of reset tokens where practical. Do not email passwords.

## Sessions

Configure session cookies with `HttpOnly`, `Secure` when HTTPS is enabled, and an appropriate `SameSite` policy. Regenerate the session ID after login and privilege changes. Set sensible session lifetime and logout behaviour. Do not put secrets in client-side storage.

## Login protection

Validate credentials, account status, and approval status. Apply rate limiting or progressive delays to repeated failures. Avoid account-enumeration messages. Log security-relevant events without recording passwords or tokens.

## Permissions

Use explicit permissions such as `users.view`, `users.add`, `users.edit`, and `users.delete`. Check permissions before processing actions. Enforce record-level access where users should see only their own or assigned records. Protect critical administrative actions, including changes that could remove the last active administrator.

## CSRF and validation

Use CSRF tokens on state-changing requests. Validate all input on the server. Apply output escaping when rendering user-controlled values.

## Audit and timestamps

Log important login, role, permission, and account changes. Use PHP-generated timestamps after setting the application timezone. Do not log passwords, reset tokens, session identifiers, or other secrets.
