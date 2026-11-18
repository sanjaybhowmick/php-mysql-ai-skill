# Configuring the Skill

The defaults are designed around the original maintainer's PHP/MySQL workflow. Public users should adapt them to their own project and security requirements.

## Common settings to review

### PHP architecture

Default: PHP 8.x, procedural PHP, MySQLi.

If your team uses an MVC structure, a framework, PDO, or object-oriented PHP, update `SKILL.md` and the relevant references. Do not leave contradictory instructions.

### SQL query policy

The maintainer's preferred approach is traditional MySQLi queries with rigorous escaping. Prepared statements are the safer general recommendation.

If you use prepared statements by default, update the database query policy in:
- `SKILL.md`
- `references/global-development-preferences.md`
- `references/database-standards.md`
- `references/php-coding-standards.md`

### Timezone

Default: `Asia/Kolkata`.

Change this in the global preferences and relevant configuration/architecture references if your project uses another timezone. For multi-timezone applications, document storage and conversion rules rather than merely changing the default string.

### UI

Default: Bootstrap 5, restrained design, local assets, no gradients, and no DataTables. Adapt the UI reference if your project uses another design system.

### Dependencies

List required libraries, pinned versions, licences, and local paths in your project documentation. Avoid relying on a CDN for critical application functionality.

## Project-specific instructions

Keep project-specific business requirements in the project repository, not in the generic skill. The skill defines development conventions; project documentation defines what the application must do.

## Technology versions

Use [`references/technology-versions.md`](../references/technology-versions.md) as the single source of truth for default technology families, exact-version selection, compatibility checks, and upgrade policy. Record exact versions for each application in that project's own dependency files and documentation. Do not change the skill defaults to match a one-off client project.
