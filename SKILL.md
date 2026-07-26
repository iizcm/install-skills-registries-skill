---
name: install-skills-registries
description: "Install agent skills from external registries (ClawHub, skills.sh, OpenClaw) into Hermes. Registries hand out `openclaw skills install` commands or redirect to GitHub; Hermes needs a raw SKILL.md URL instead. Use when the user links a skill from clawhub.ai or skills.sh and wants it installed in Hermes."
version: 1.0.0
author: Community
license: MIT
platforms: [linux, macos, windows]
tags: [general]
---

# Install Skills Registries — Skill

Install agent skills from external registries (ClawHub, skills.sh, OpenClaw) into Hermes. Registries hand out `openclaw skills install` commands or redirect to GitHub; Hermes needs a raw SKILL.md URL instead. Use when the user links a skill from clawhub.ai or skills.sh and wants it installed in Hermes.

## Install

```bash
cp -r <skill-name> ~/.hermes/skills/<skill-path>/
```

Or clone this repository:

```bash
git clone https://github.com/iizcm/install-skills-registries-skill.git ~/.hermes/skills/<skill-path>/
```

## Usage

Invoke your AI agent with a clear instruction matching this skill's purpose. The agent will route tasks to this skill when the instruction matches its description or trigger keywords.

Refer to `README.md` in this repository for:
- Detailed step-by-step installation guide
- Bilingual documentation (English + Indonesian)
- Troubleshooting table
- Security best practices
- Customization tips

## Safety rules

- Never commit private keys, seed phrases, API tokens, or personal data to version control
- Use placeholders (`<YOUR_...>`) in all examples and code snippets
- Validate all outputs before acting on them
- Keep real credentials in your runtime's secure credential store only
