# Technology Versions and Compatibility Policy

## Purpose

This document is the single source of truth for the skill's technology-version policy and default technology families. Update this file when changing the skill's defaults. Other documents should describe how to use a technology, not maintain competing version numbers.

These are skill defaults, not a requirement to upgrade an existing application. The actual versions used by a project must be recorded in that project's own documentation and dependency/configuration files.

## Default technology policy

| Technology | Skill default | Project-level rule |
|---|---|---|
| PHP | PHP 8.x; choose and pin a supported minor version per project | Match the hosting/runtime environment and the project's compatibility requirements |
| MySQL | MySQL; choose a supported server version per project | Confirm compatibility with the actual MySQL or MariaDB server before using vendor-specific features |
| MySQLi | PHP MySQLi extension | Confirm the extension is installed and enabled in the target PHP runtime |
| Bootstrap | Bootstrap 5.x | Pin the exact release used by the project; do not mix files from different releases |
| jQuery | jQuery 3.x when needed | Use only where useful, mainly for non-tabular interactions; pin the exact release |
| Font Awesome | Optional; use only when useful | Pin the exact release and confirm icon names/classes against that release |
| PHPMailer | Optional SMTP mail library | Pin the exact release; prefer Composer or a documented local installation |
| HTML, CSS, JavaScript | Current browser-supported standards | Test against the browsers and devices supported by the project |

The version families above are compatibility baselines for this skill, not claims that they are the latest available releases. Do not invent exact patch versions.

## Rules for selecting versions

1. For a new project, identify the target hosting/runtime environment before selecting exact versions.
2. Check official release and support information when the user asks for the latest version, when selecting a new exact version, or when compatibility is uncertain.
3. Prefer supported, security-maintained releases that are compatible with the target environment and the other project dependencies.
4. Record exact versions in the project's README, dependency manager files, deployment documentation, or a dedicated project technology manifest.
5. For Composer-managed PHP libraries, use `composer.json` and `composer.lock` as the dependency source of truth. Do not edit the lock file manually.
6. For locally hosted frontend libraries, keep the versioned files together and document their source and version. Avoid silently mixing CDN and local versions.
7. Do not upgrade dependencies in an existing project merely because a newer release exists. First inspect the current versions, review breaking changes, assess compatibility, and obtain the user's approval for a material upgrade.
8. Do not describe a version as latest or supported unless that status has been checked against an authoritative source.

## Existing project discovery

Before writing or changing code, inspect the project's actual environment and dependency declarations where available, including:

- `php -v` and enabled PHP extensions (`php -m`), plus the web-server PHP runtime where it may differ from CLI PHP.
- `composer.json` and `composer.lock`.
- Database server version and vendor (MySQL or MariaDB).
- Frontend library files, package manifests, asset directory names, and existing documentation.
- Hosting or deployment configuration that constrains available versions.

If the actual version cannot be established, ask the user or state the assumption. Do not silently select a version that may be incompatible.

## Updating this skill's defaults

When the maintainer changes a default version or supported technology family:

1. Edit this file first.
2. Update `SKILL.md` only if the default technology family or stack description changes; keep it concise and point agents to this document.
3. Update technical reference documents only where behaviour, syntax, APIs, or compatibility guidance changes. Avoid repeating exact version numbers there.
4. Update `README.md` and `CHANGELOG.md` when the public-facing defaults or release contents change.
5. Search the repository for old version numbers and conflicting instructions before committing.
6. Test relevant examples against the declared versions before claiming compatibility.

## Project-specific override

A project's explicit requirements and actual installed environment take precedence over these skill defaults, unless they conflict with a higher-priority user instruction or create a material security risk. Document project-specific overrides in that project's own instructions or README. Never modify this central skill document just to record one client's project versions.
