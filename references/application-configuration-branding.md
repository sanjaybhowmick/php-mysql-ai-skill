# Application Configuration and Branding

## Two configuration layers

Keep these separate:

1. **System configuration:** database credentials, environment, application URL, session settings, storage paths, and technical security settings. Keep these in protected configuration or environment variables.
2. **Administrator-managed settings:** application name, logo, favicon, colours, fonts, timezone, date/time formats, and pagination defaults. Store these in the database when appropriate.

Never expose secrets through an administrator settings page.

## Suggested structure

```text
config/
  config.php
  database.php
  constants.php
  email.php
includes/
  settings.php
  branding.php
modules/settings/
  general.php
  branding.php
  regional.php
  preferences.php
```

## Settings storage

A key-value `app_settings` table can be suitable for modest applications. Use unique keys, setting groups, update metadata, and indexes. Use dedicated tables when settings become relational or complex. Do not store passwords, API secrets, or database credentials in this table.

## Branding

Support application name, logo, favicon, primary/secondary/accent colours, body/content backgrounds, text colours, and heading/body fonts. Validate colour values against an explicit format such as six-digit hexadecimal. Restrict fonts to known system stacks or approved locally hosted font files. Never accept arbitrary CSS, HTML, or JavaScript.

Generate centrally controlled CSS variables from validated settings. Use no gradients or flashy styling. Keep the design minimal and readable.

## Timezone and formats

Default timezone: `Asia/Kolkata`. Validate selected timezones using `DateTimeZone::listIdentifiers()`. Set the PHP timezone before generating timestamps. Store database dates in consistent machine formats and format them only for display. For multi-timezone systems, explicitly define UTC storage and display conversion.

## Pagination preferences

Allow only approved page sizes, such as 10, 20, 50, and 100. The configured page size must not disable server-side pagination.

## Uploads and audit

Use the file-management standards for logo and favicon uploads. Record important setting changes with previous/new values, actor, and application timestamp, excluding secrets.

## Loading and caching

Load settings once per request where practical. Invalidate any persistent cache after updates. Validate stored values when loading them; database content is not automatically trusted.
