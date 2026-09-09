# Skills

AI agent skills in `SKILL.md` format. They work with Claude Code, Codex, Cursor, and any agent that reads skills.

Install:

```bash
npx skills@latest add johnsonAyo/skills
```

## Skills

| Skill | Purpose |
| --- | --- |
| `replace-dont-layer` | Change the existing behaviour owner and remove superseded code. |

## replace-dont-layer

Before adding behaviour, the agent finds the code that already owns it, changes or replaces that source, and removes what the new behaviour supersedes.
