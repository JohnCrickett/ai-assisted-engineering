## Table of Contents

- [Coding Agent Skills](#coding-agent-skills)
  - [What Are Agent Skills?](#what-are-agent-skills)
  - [What Are Skills Used For?](#what-are-skills-used-for)
    - [Example Skills](#example-skills)
    - [Where Are Skills Found / Installed](#where-are-skills-found--installed)
  - [How Are Skills Invoked?](#how-are-skills-invoked)
  - [How To Create Skills](#how-to-create-skills)
  - [References](#references)

# Coding Agent Skills

Skills are modular capabilities that extend a coding agent’s functionality.

## What Are Agent Skills?

Agent Skills package expertise into discoverable capabilities. Each Skill consists of a `SKILL.md` file with instructions that an Agent reads when relevant, plus optional supporting files like scripts and templates.

## What Are Skills Used For?

Skills are reusable tools that give coding agents specialized capabilities and make the coding agents more modular and maintainable. You can add new capabilities by creating new skills, update existing ones without touching the agent's core logic, and even share skills across different agents or projects. When an agent needs to run tests, format code, or deploy to production, it's calling on pre-built skills that handle the complexity behind a simple interface.

### Example Skills

- **GitHub Operations**: Create issues, open pull requests, review code, merge branches
- **Code Review**: Analyze code changes for bugs, suggest improvements, check style compliance, verify test coverage
- **Code Analysis**: Run linters, check test coverage, detect security vulnerabilities
- **Testing**: Execute unit tests, run integration tests, generate test reports
- **Environment Management**: Set up development environments, install dependencies, configure build tools
- **Documentation**: Generate API docs, update README files, create changelog entries
- **Deployment**: Build containers, push to registries, trigger CI/CD pipelines
- **Database Operations**: Run migrations, seed test data, backup databases
- **Code Generation**: Scaffold new files, generate boilerplate, refactor existing code

### Where Are Skills Found / Installed

Some agents support personal (local user) and project based skills. 

Use personal Skills for:

- Your individual workflows and preferences.
- Experimental Skills you’re developing.
- Personal productivity tools, not limited to a specific project, or even to coding.

Use project Skills for:

- Team workflows and conventions.
- Project-specific expertise.
- Utilities and scripts to be used by everyone working on the project.
- Project Skills should be checked into git and automatically available to team members.

Skills are installed in diffent locations depending on the agent being used and the scope of the skills.

| Agent | Personal Skills | Project Based Skills |
|-|-|-|
| **Amp** | ~/.claude/skills/ or ~/.config/amp/tools | .claude/skills/ |
| **Claude Code** | ~/.claude/skills/ | .claude/skills/ |
| **OpenAI Codex** | ~/.codex/skills/ | |

## How Are Skills Invoked?

Skills are model-invoked—Claude autonomously decides when to use them based on your request and the Skill’s description. This is different from slash commands, which are user-invoked (you explicitly type /command to trigger them).

Benefits:

- Extend Claude’s capabilities for your specific workflows.
- Share expertise across your team via git.
- Reduce repetitive prompting.
- Compose multiple Skills for complex tasks.

## How To Create Skills

Skills are stored as directories containing a SKILL.md file and some optional supporting files.

A SKILL.md file has the following format:

```
---
name: skill-name
description: A brief description of the Skill, what it does and when to use it
---

# Skill Name

## Instructions
Provide clear, step-by-step guidance for the coding agent.

## Examples
Show concrete examples of using this Skill.
```

Claude Code optionally also supports a field `allowed-tools:` which if specified in the frontmatter limits the tools that can be used whilst the skill is active.

Skills can be built with supporting files, that can be referenced from the SKILLS.md

```
my-skill/
├── SKILL.md (required)
├── reference.md (optional documentation)
├── examples.md (optional examples)
├── scripts/
│   └── helper.py (optional utility)
└── templates/
    └── template.txt (optional template)
```

## References

- [Claude Code Skills](https://code.claude.com/docs/en/skills)
- [Claude Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [Amp Agent Skills](https://ampcode.com/manual#agent-skills)
- [OpenAI Codex Skills](https://github.com/openai/codex/blob/main/docs/skills.md)
