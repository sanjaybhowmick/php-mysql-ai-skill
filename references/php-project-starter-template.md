# Reusable PHP Project Starter Template

## Purpose

Create a reusable foundation for custom PHP/MySQL applications. Keep common infrastructure separate from project-specific business modules. Do not turn the starter into a rigid framework.

## Core components

A starter may include:
- Central configuration and MySQLi connection.
- Secure initialisation and common functions.
- Login/logout and password handling.
- Users, roles, and permissions.
- Dashboard and shared Bootstrap layout.
- Central branding/settings.
- CSRF and validation helpers.
- Server-side pagination.
- Activity and error logging.
- File-management foundation.
- PHPMailer integration.
- Database installation SQL and migrations.
- Project documentation.

Payment gateways, PDF generation, spreadsheets, WhatsApp, advanced reporting, and other integrations should be added only when required.

## Suggested structure

```text
project/
├── public/                 # Preferred web document root
│   ├── index.php
│   ├── assets/
│   └── uploads-public/     # Only if truly public and safe
├── admin/
├── config/
├── includes/
├── modules/
├── ajax/
├── libraries/
├── storage/
│   ├── private/
│   └── logs/
├── database/
│   ├── install.sql
│   └── migrations/
├── email-templates/
├── docs/
├── .gitignore
└── README.md
```

Adapt paths to the hosting environment. Private storage, configuration, logs, and SQL scripts must not be publicly accessible.

## Build in stages

### Stage 1: Core
- Folder structure.
- Configuration.
- Database connection.
- Initialisation.
- Common functions.
- Session security.
- Login/logout.
- Roles and permissions.
- Shared layout.

### Stage 2: Common modules
- User management.
- Branding settings.
- A reference CRUD module.
- Server-side pagination.
- Activity logging.
- File management.
- Email integration.

### Stage 3: Release readiness
- Installation SQL.
- Sample data without real credentials.
- Security review.
- Functional tests.
- Documentation.
- Deployment instructions.
- Git ignore rules.

## Generic schema candidates

Depending on project scope, common tables may include:
`users`, `roles`, `permissions`, `user_roles`, `role_permissions`, `app_settings`, `activity_logs`, and `email_logs`.

Do not add unused tables or features simply because they appear in this list.

## Reference CRUD module

Create one simple example module to demonstrate:
- List with server-side pagination.
- Search and filtering.
- Add/edit/view.
- Deactivate or delete according to business rules.
- Server-side validation.
- CSRF and permission checks.
- Safe SQL handling.
- Activity logging.

## Installation and release

Document required PHP version/extensions, database creation, configuration, migrations, storage permissions, initial administrator creation, SMTP setup, scheduled jobs, HTTPS, backups, and deployment checks. Disable or remove installation utilities after setup.

## Quality checklist

Verify a fresh installation, authentication, permissions, CSRF, server-side validation, server-side pagination, branding, timezone, file restrictions, email configuration, logging, private-file protection, and production error handling.
