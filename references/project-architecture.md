# Project Architecture Standards

## Default architecture

Use modular procedural PHP. Keep the design understandable and avoid unnecessary frameworks or abstractions.

Suggested structure:

```text
project/
├── config/
│   ├── config.php
│   ├── database.php
│   ├── constants.php
│   └── email.php
├── includes/
│   ├── init.php
│   ├── functions.php
│   ├── auth.php
│   ├── permissions.php
│   ├── csrf.php
│   ├── validation.php
│   ├── pagination.php
│   ├── header.php
│   ├── sidebar.php
│   └── footer.php
├── modules/
│   ├── users/
│   └── settings/
├── ajax/
├── assets/
│   ├── css/
│   ├── js/
│   ├── fonts/
│   └── images/
├── uploads/
├── libraries/
├── database/
│   ├── install.sql
│   └── migrations/
├── logs/
├── docs/
├── index.php
└── .htaccess
```

Prefer a dedicated public document root. If hosting requires the project root to be web-accessible, deny direct access to configuration, logs, database scripts, private uploads, and other sensitive paths.

## Initialisation

Use one predictable initialisation path:

1. Load system configuration.
2. Configure and start the session.
3. Establish the database connection.
4. Load application settings.
5. Validate and set the application timezone.
6. Load shared functions and security helpers.
7. Initialise authentication when required.

Login and public pages must be able to initialise without requiring an authenticated session.

Avoid circular includes. Use `__DIR__` and `require_once`.

## Modules

Keep each business module in its own directory. Use consistent page responsibilities, for example `list.php`, `add.php`, `edit.php`, `view.php`, and action handlers. Do not force this exact structure when a smaller or different arrangement is clearer.

Keep AJAX endpoints separate and protect them independently.

## Shared components

Centralise database connection, authentication, permissions, CSRF, validation, pagination, branding, email, logging, and layout components. Reuse functions rather than duplicating logic.

## Database and deployment

Keep installation SQL and incremental migrations under version control. Document environment configuration, required PHP extensions, permissions, scheduled jobs, and deployment steps. Never commit production secrets or private user uploads.

## Existing applications

Inspect the current architecture before making changes. Do not restructure an established application just to match this example. Prefer incremental, compatible changes.
