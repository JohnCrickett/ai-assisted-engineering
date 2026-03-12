# How To Pair With An AI Coding Agent

## Introduction

Pairing with an AI coding agent is a skill. Like any skill, you get better at it with practice and good technique.

## The Core Mindset

The biggest mistake developers make is treating an AI agent like a vending machine. Put in a vague request, expect working software to come out.

That's not how it works.

Think of the agent as a fast, capable inexperienced developer. It can write a lot of code, hold a lot of context, and never gets bored of boilerplate. But it needs direction. It needs feedback. It needs someone to catch its mistakes.

That person is you. Your job is still to:

- Understand the problem before handing anything off.
- Provide guardrails and ideally, automated checks.
- Review every suggestion critically, not just skim it.
- Catch logic errors, bad assumptions, and code that looks right but isn't.
- Make the final call on architecture and trade-offs.

## Before You Start

A little prep makes a big difference.

**Give the agent context.** Don't just paste a task. Tell it what the codebase does, what constraints matter, and what done looks like. The more relevant context you provide upfront, the less back-and-forth you'll need later.

**Provide automated verification.** Give the agent automated tools to check it's work, that includes compilers, linters, static analysis and automated tests.

**Be specific about scope.** "Add a login feature" is too vague. "Add a login endpoint that accepts email and password, validates against the users table, and returns a JWT" is a real task. Treat the prompt like a specification.

**Point it at the right files.** Agents can read your project, but directing them to the relevant code saves time and reduces the chance of the agent sucking in irrelevant context.

## Key Points

AI agents amplify what you bring to the table. If you understand the problem well, they help you move fast. If you don't, they help you produce the wrong thing faster.

Treat prompts like specifications for tasks and features. Review everything. Stay in control.

The agent is a tool. You're the software engineer.
