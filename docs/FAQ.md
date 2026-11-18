# FAQ

## Does this skill generate a complete application automatically?

No. It provides development standards and workflow guidance. The AI agent still needs your requirements, project files, database context, and review.

## Can I use it with an existing PHP application?

Yes. The workflow requires the agent to inspect existing files and preserve established behaviour before making changes.

## Must I use procedural PHP?

No. Procedural PHP is the default preference. You can adapt the skill for OOP, MVC, or a framework by updating its instructions.

## Why does the SQL guidance discuss prepared statements?

Prepared statements are generally safer for dynamic values. The original maintainer prefers escaped traditional MySQLi queries, so the skill documents that preference while clearly explaining its limitations.

## Why is pagination server-side?

Large datasets should not be loaded into the browser merely to paginate or filter them. Database-side pagination and filtering reduce unnecessary transfer and client processing.

## Does the skill require Asia/Kolkata?

That is the default. Change it for your application and document the timestamp storage strategy.

## Can I use it with tools that do not support Agent Skills?

Yes. Use the tool-neutral fallback in `AI-TOOLS.md` and point the agent to `SKILL.md` and the reference directory.

## Is generated code production-ready?

Not automatically. Review, test, configure, and secure all generated code before deployment.
