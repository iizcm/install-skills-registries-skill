---
name: install-skills-registries
description: Install agent skills from external registries (ClawHub, skills.sh, OpenClaw) into Hermes. Registries hand out `openclaw skills install` commands or redirect to GitHub; Hermes needs a raw SKILL.md URL instead. Use when the user links a skill from clawhub.ai or skills.sh and wants it installed in Hermes.
---

# Install Skills from External Registries into Hermes

## Key fact
Hermes install takes a direct URL to a SKILL.md file (or `user/repo/path`):
`hermes skills install "<raw-url>/SKILL.md" --name <name> --force --yes`
Registries like ClawHub show `openclaw skills install @user/skill` (OpenClaw format) — that does NOT run in Hermes. Convert to a raw GitHub URL.

## Find the raw SKILL.md URL
Both clawhub.ai and skills.sh ultimately point at GitHub repos.
1. ClawHub skill page → copy the install command, extract `@owner/skill`.
2. Resolve the raw path via GitHub API tree:
   `curl "https://api.github.com/repos/<owner>/<repo>/git/trees/main?recursive=1" | grep SKILL.md`
3. Common layouts observed:
   - `vercel-labs/skills` → `skills/<name>/SKILL.md`
   - `vercel-labs/agent-skills` → `skills/<name>/SKILL.md`
   - `anthropics/skills` → `skills/<name>/SKILL.md`
4. Raw URL: `https://raw.githubusercontent.com/<owner>/<repo>/main/<path>/SKILL.md`

## Install
`hermes skills install "https://raw.githubusercontent.com/<owner>/<repo>/main/<path>/SKILL.md" --name <name> --force --yes`

## Pitfalls
- skills.sh pages 308-redirect to `www.skills.sh` and then to `github.com/<org>/skills` — follow to GitHub, don't scrape the HTML.
- Branch may be `main` not `master`; confirm via `api.github.com/repos/<owner>/<repo>` → `default_branch`.
- If Hermes rejects the SKILL.md (no `name:` frontmatter), pass `--name <fallback>`.
- Skills installed this way show as `url / community` in `hermes skills list` — that's expected.
