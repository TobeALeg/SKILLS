---
name: lw
description: Explicit short command for operating the project-local LLM Wiki. Use only when the user invokes /lw or $lw to initialize, update, query, inspect, or validate project memory.
---

# LW

Treat `/lw` as the short, explicit interface to the sibling `llm-wiki` skill. Do not activate this alias implicitly.

Resolve the engine as `../llm-wiki/scripts/wiki.py` relative to this skill directory. Find the project root using the current working directory unless the user supplies another path.

## Commands

- `/lw` or `/lw update`: initialize the wiki if needed, summarize the durable facts from the relevant current conversation, and run `update` with that episode.
- `/lw init`: initialize `.llm-wiki/` without calling the external model.
- `/lw status`: show pending project files, episodes, page count, and last update.
- `/lw ask <query>`: run `context <query>` and answer from the returned pages.
- `/lw scan`: show file changes without calling the model.
- `/lw lint`: validate Wiki consistency.

For an update, retain decisions, rationale, constraints, corrections, durable facts, and open questions. Exclude unrelated chat, hidden reasoning, and secrets. Pass structured conversation context through a temporary episode JSON file or a safely quoted `--episode` value.

Read the sibling `llm-wiki/SKILL.md` before performing an update or when handling an error. Its storage, provenance, secret-exclusion, and external-model rules remain authoritative.
