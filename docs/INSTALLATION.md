# Installation

## Option 1: Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/custom-php-mysql-development.git
```

Replace the example repository URL with the actual public GitHub URL.

## Option 2: Download ZIP

On GitHub, select **Code → Download ZIP**, then extract the archive.

## Use the skill in a project

Keep the skill repository outside the production web root. Copy it into a project-specific agent skills directory or reference it from the tool's supported instruction file.

Do not copy the skill into a publicly served PHP directory unless the web server is configured to deny access to Markdown and repository files.

## Verify the installation

Confirm that the project contains:
- `SKILL.md`
- `references/`
- All Markdown reference files

Ask the AI agent:

> Read the custom PHP and MySQL development skill. Summarise its technology defaults, SQL safety policy, pagination rule, timezone rule, and security requirements. Do not modify files yet.

Review the summary to confirm that the agent has loaded the instructions.

## Updating

Pull the latest repository changes or download a new release. Review changes before replacing a customised local copy. Keep project-specific changes in a separate file where possible so upstream updates are easier to merge.
