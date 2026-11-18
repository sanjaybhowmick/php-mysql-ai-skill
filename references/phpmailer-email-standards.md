# PHPMailer and Email Standards

## Library and transport

Use PHPMailer with authenticated SMTP. Prefer a locally managed, version-pinned dependency installed through Composer or an approved local library installation. Do not load PHPMailer from a CDN.

## Configuration

Keep SMTP host, port, encryption, username, password, sender, and reply-to settings in protected configuration or environment variables. Never place credentials in public repositories, browser code, or general application settings.

## Reusable sending service

Create one reusable email function/service that:
- Configures SMTP.
- Validates recipients.
- Sets sender and reply-to.
- Supports HTML and plain-text alternatives.
- Adds validated attachments.
- Sends the message.
- Logs a safe result.
- Returns a predictable success/failure result.

Do not expose SMTP error details to ordinary users.

## Templates

Keep templates separate from business logic. Use consistent application branding, simple responsive HTML, and inline CSS where email-client compatibility requires it. Avoid JavaScript and unnecessary external assets. Escape dynamic values for HTML context and validate URLs. Use the configured application URL, not an untrusted Host header.

## Attachments

Accept trusted server-side file references, not arbitrary user-supplied filesystem paths. Check file existence, readability, size, type, and permission. Do not attach executables or confidential files without authorisation. Clean up temporary files.

## Security and reliability

Validate email addresses and prevent header injection. Rate-limit user-triggered messages. Never email passwords or reusable reset tokens. Use short-lived, single-use reset links.

A successful PHPMailer send means the SMTP server accepted the message; it does not prove inbox delivery.

## Logging

Log recipient, subject or template identifier, message type, status, safe error category, actor, and timestamp as appropriate. Do not log SMTP passwords, reset tokens, session IDs, or sensitive message contents.

## Queue

For higher-volume applications, use a database-backed queue with pending/processing/sent/failed states, retry limits, processing locks, and scheduled processing. Direct sending may be adequate for small applications.
