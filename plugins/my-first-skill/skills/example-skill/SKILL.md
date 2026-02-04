---
name: example-skill
description: >
  A minimal example skill. Invoked via `/example-skill` to demonstrate
  how skills are structured and called within Claude Code.
usage: /example-skill [message]
examples:
  - command: /example-skill Hello
    description: Echoes back "Hello" with a greeting.
---

# Example Skill

This is a template skill for the `my-first-skill` plugin.

## What this skill does

When invoked, it:

1. Acknowledges the invocation.
2. Echoes back any message the user provides.
3. Prints a usage hint if no message is given.

## Implementation notes

- Replace the content below with your actual skill logic.
- Skills can call tools (Bash, Read, Write, etc.) just like any other Claude Code prompt.
- Keep the YAML frontmatter (`name`, `description`, `usage`) up to date.

## Behavior

- If the user provides a message after `/example-skill`, repeat it back with a greeting.
- If no message is provided, respond with a short help text showing correct usage.
