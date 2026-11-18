# Custom PHP and MySQL Development Skill

A reusable AI coding skill for planning, building, maintaining, and troubleshooting custom PHP 8.x and MySQL applications.

It provides practical development standards for procedural PHP, MySQLi, Bootstrap 5, security, CRUD modules, server-side pagination, file handling, email, project architecture, and AI-assisted development workflows.

## Who is this for?

- PHP developers using AI coding assistants.
- Teams maintaining procedural PHP/MySQL applications.
- Developers who want consistent project conventions across AI tools.
- People starting custom admin panels and business applications.

## What is included?

- `SKILL.md` — the main agent instructions.
- `references/` — detailed technical standards.
- `docs/` — installation, tool-specific usage, configuration, security, and FAQ.
- `examples/` — project instruction and prompt examples.

## Quick start

1. Download or clone this repository.
2. Read [Installation](docs/INSTALLATION.md).
3. Follow the instructions for your AI tool in [AI Tools](docs/AI-TOOLS.md).
4. Add the skill to your project or agent's skill directory.
5. Ask the agent to read the skill before implementing PHP/MySQL work.

## Core defaults

- PHP 8.x, MySQL, MySQLi.
- Procedural PHP by default.
- Bootstrap 5.
- jQuery for non-tabular interactions only.
- Server-side pagination for database listings.
- Server-side validation for every form.
- Central configuration and branding.
- Default timezone `Asia/Kolkata`.
- Prefer local dependencies over CDN dependencies.
- Minimal, professional UI without gradients or flashy styling.

### SQL safety note

The original maintainer prefers traditional MySQLi query execution with rigorous escaping. This is not as robust as prepared statements. The skill explains both approaches and recommends prepared statements for users who do not have an established query-style preference. Never concatenate untrusted input into SQL.

## Customisation

Read [Configuration](docs/CONFIGURATION.md) before adapting the skill. You can change the default timezone, query policy, architecture, UI conventions, and dependency preferences to match your team.

## Compatibility

The skill is written as a portable `SKILL.md` plus Markdown reference files. It can be used by tools that support Agent Skills or by manually adding its instructions to a project's agent instruction file. Exact discovery and installation behaviour differs by tool; see [AI Tools](docs/AI-TOOLS.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Please keep instructions tool-neutral where possible and document tool-specific setup separately.

## Licence

Released under the MIT License. See [LICENSE](LICENSE).

## Disclaimer

This repository provides development guidance, not a guarantee that generated code is secure or production-ready. Review, test, and adapt all code before deployment. Security-sensitive systems require qualified review.
