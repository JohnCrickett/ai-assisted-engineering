# Requirements

## Refining Requirements

A big challenge in software engineering is vague, ambiguous and incomplete requirements. AI can be use to help with this. A good process is:

1. Start a new session with a fresh, clear context window.
2. Set the scene for the AI agent, tell it what role it is to play and what you require it to do.
3. Provide the current known requirements and any relevant details.
4. Instruct it to ask you questions in order to clarify the requirements.
5. Answer the questions and instruct it to ask any more questions if needed.
6. Repeat 5 until the agent has the information it ask for.
7. Ask the agent to write out the requirements in your required format, i.e. markdown.

### Example Prompt Template

```text
You are a software engineer tasked with building a system to <GOAL>. 
Your current task is to draft a set of requirements for <TASK/FEATURE>.

These are the currently documented requirements: <INSERT DRAFT REQUIREMENTS>.

Ask me all the questions you need answers to in order to create a complete set of 
requirements and acceptance criteria?
```

### Example Response Template

```text
Here are the answers to your questions:

1. <ANSWER 1>
2. <ANSWER 2>

What additional questions do you need answered?
```

### Requirements Format

For best results include in the initial prompt for requirements one or more examples of the required requirements format. For example I prefer to use EARS, my prompt therefore includes the additional text:

```text
Use the The Easy Approach to Requirements Syntax for the requirements.

The Easy Approach to Requirements Syntax (EARS) is a mechanism to gently constrain textual requirements. The EARS patterns provide structured guidance that enable authors to write high quality textual requirements.

Generic EARS syntax: 

The clauses of a requirement written in EARS always appear in the same order. The basic structure of an EARS requirement is:

While <optional pre-condition>, when <optional trigger>, the <system name> shall <system response>

The EARS ruleset states that a requirement must have: Zero or many preconditions; Zero or one trigger; One system name; One or many system responses.
```
