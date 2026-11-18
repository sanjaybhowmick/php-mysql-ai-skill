# Using the Skill with Different AI Coding Tools

This repository follows the portable Agent Skills folder convention: a skill directory contains `SKILL.md` and may include `references/`, `scripts/`, and other supporting files.

The same folder can be installed in several tools. Exact support and discovery paths vary by product and version; the instructions below reflect the official documentation checked for this release. Recheck the linked documentation when upgrading your tools.

## 1. Codex

Codex discovers repository skills from `.agents/skills/` and personal skills from `~/.agents/skills/`.

### Install for one project

Run these commands from the root of your PHP project:

```bash
mkdir -p .agents/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .agents/skills/custom-php-mysql-development
```

### Install for your user account

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  ~/.agents/skills/custom-php-mysql-development
```

The user-level installation makes the skill available across projects in supported Codex environments.

### Use it

Start Codex in your PHP project and ask:

> Use the custom-php-mysql-development skill. Read SKILL.md and the relevant reference documents before modifying the project.

If Codex does not list a newly installed or changed skill, restart the session. See the official [Codex skill documentation](https://learn.chatgpt.com/docs/build-skills).

## 2. Claude Code

Claude Code supports project-level and personal skills. Each skill is a folder containing `SKILL.md`.

### Install for one project

From the root of your project:

```bash
mkdir -p .claude/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .claude/skills/custom-php-mysql-development
```

### Install for your user account

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  ~/.claude/skills/custom-php-mysql-development
```

### Use it

Start Claude Code in the project. The skill can be selected/invoked as:

```text
/custom-php-mysql-development
```

Or ask Claude to use the skill when describing your task. Check the available skills with `/skills`.

Project skills can be committed to Git so the team shares the same version. See [Claude Code skills documentation](https://code.claude.com/docs/en/skills).

## 3. Cursor

Cursor supports Agent Skills. Current documented project-level skill locations include `.agents/skills/` and `.cursor/skills/`. It also recognises compatible Claude and Codex skill directories.

### Recommended project installation

From the root of your project:

```bash
mkdir -p .agents/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .agents/skills/custom-php-mysql-development
```

Alternatively, install under `.cursor/skills/`:

```bash
mkdir -p .cursor/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .cursor/skills/custom-php-mysql-development
```

### Use it

Open the project in Cursor. The skill should be discovered automatically. You can invoke it from Agent chat by typing `/` and selecting the skill, or ask Agent to use it.

Cursor also supports project rules in `.cursor/rules/*.mdc`. Use a rule only if you need additional always-on project guidance; do not duplicate the entire skill in a rule.

See [Cursor Agent Skills](https://cursor.com/docs/skills) and [Cursor Rules](https://cursor.com/docs/rules).

## 4. Gemini CLI

Gemini CLI supports Agent Skills and discovers workspace skills from `.agents/skills/` or `.gemini/skills/`.

### Recommended project installation

From the root of your project:

```bash
mkdir -p .agents/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .agents/skills/custom-php-mysql-development
```

Alternative:

```bash
mkdir -p .gemini/skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .gemini/skills/custom-php-mysql-development
```

### Use it

Start Gemini CLI in the project. The CLI discovers skills from its supported locations. You can inspect the available skills using:

```text
/skills list
```

Gemini CLI may ask for consent before activating a skill because activation grants it access to the skill directory. Review the prompt before approving.

See the official [Gemini CLI Agent Skills guide](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/skills.md).

## 5. GitHub Copilot

GitHub Copilot supports repository-wide custom instructions through `.github/copilot-instructions.md`. This is an instruction-file integration rather than the same automatic skill discovery flow described above.

### Install the skill in the repository

For example, clone the skill into:

```bash
mkdir -p .ai-skills
git clone https://github.com/sanjaybhowmick/php-mysql-ai-skill.git \
  .ai-skills/custom-php-mysql-development
```

Create `.github/copilot-instructions.md`:

```markdown
For PHP and MySQL development, follow the skill at:

`./.ai-skills/custom-php-mysql-development/SKILL.md`

Read the relevant reference documents in that skill's `references/`
directory before implementing a feature.

Inspect the existing project first. Preserve existing behaviour.
Use server-side validation, security checks, and server-side pagination.
Do not claim tests passed unless they were actually run.
```

For Copilot clients that support file references, you can also include:

```markdown
@.ai-skills/custom-php-mysql-development/SKILL.md
```

The main skill instructs the agent to load relevant reference files. Confirm that your Copilot client can access the repository files in the current mode.

See [GitHub Copilot custom instructions](https://docs.github.com/en/copilot/concepts/prompting-and-context/custom-instructions).

## 6. Other Agent Skills-compatible tools

If another coding agent supports the Agent Skills convention, install the complete folder in the skill directory documented by that product.

The required structure is:

```text
custom-php-mysql-development/
├── SKILL.md
└── references/
    ├── global-development-preferences.md
    └── ...
```

If the tool does not support Agent Skills, use its project instruction mechanism (`AGENTS.md`, `GEMINI.md`, `CLAUDE.md`, or equivalent) to point to `SKILL.md` and instruct the agent to read relevant references.

Do not assume that every product recognises every instruction filename.

## 7. Verify that the skill is active

After installation, ask the agent:

> Read the custom-php-mysql-development skill. Summarise its PHP architecture, SQL safety policy, server-side pagination requirement, timezone default, UI rules, and mandatory security checks. Do not edit any files.

Check that the answer reflects the repository's current contents.

Then try a small, low-risk task and inspect the proposed changes before allowing a larger implementation.

## 8. Updating the skill

If installed through Git:

```bash
cd path/to/custom-php-mysql-development
git pull
```

Review local changes before pulling. If you have customised the skill, keep your changes in a separate branch or maintain a project-specific override file to reduce merge conflicts.

## Official documentation

- [Codex: Build skills](https://learn.chatgpt.com/docs/build-skills)
- [Claude Code: Skills](https://code.claude.com/docs/en/skills)
- [Cursor: Agent Skills](https://cursor.com/docs/skills)
- [Cursor: Rules](https://cursor.com/docs/rules)
- [Gemini CLI: Agent Skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/skills.md)
- [GitHub Copilot: Custom instructions](https://docs.github.com/en/copilot/concepts/prompting-and-context/custom-instructions)
