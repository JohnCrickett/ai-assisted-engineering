# Prompt Engineering

## Introduction

Prompt engineering is the craft of giving an LLM the right information, structure, and constraints so it produces useful output. If you use AI to write or review code, or you are building software on top of LLMs, prompting becomes part of your daily workflow and prompt engineering is a key skill to develop. You can think of prompting as writing a small specification, and Prompt Engineering as the practice and skill of doing so effectively.

The goal of this guide is show you how prompting works, and to teach you the core techniques. Having worked through it you will be able to write prompts that produce accurate, useful results.

---

## Why Prompt Engineering Matters

LLMs are powerful, but they are not mind readers. A vague prompt produces vague output. When prompting badly, software engineers run into the same issues again and again:

* Code that compiles but does not match the requirements
* Missing edge cases
* Overconfident answers
* Half finished solutions

The fix is almost always a better prompt.

Two quick examples:

**Weak prompt:**
`Write a function to sort a slice in Go.`

**Strong prompt:**
`Write a function to sort slices in Go. The slices may contain structs. The sort order may refer to multiple fields in the struct.  Just show the final code for the function. Do not include an example of the usage.`

The second version acts like a precise spec. The model follows your lead.

---

## How LLMs Use Prompts

Here's a simple way to think of prompting: everything in the prompt becomes the model’s temporary memory. It predicts what comes next using that memory. Examples become patterns the model tries to copy. Constraints guide the output. Tone and rules shape the style or the output.


---

## System Prompts vs User Prompts

There are two types of prompts: system prompts and user prompts. System prompts define the rules, behaviour, and constraints for the model. User prompts specify the task you want the model to perform.

In an application, the system prompt becomes part of your applications configuration. The user prompt becomes the input from your user.

In a chat application or your coding agent the system prompt has been provided by the developer of the tool and your input is the user prompt.

**Example:**

System prompt:
You are a backend engineering assistant. Your answers must be short, accurate, and use production ready code only.

User prompt:
Write a PostgreSQL migration that creates a sessions table with a composite primary key.

This separation becomes essential when you build LLM powered tools.

---

## Examples

Examples are concrete demonstrations of the task you want the model to perform. You provide input and the corresponding output so the model can learn the pattern from context.

This is known as in-context learning. By seeing examples, the model doesn’t just rely on the instructions—it infers the format, style, and structure you expect. Examples are especially useful when you want:

- Consistent output formatting
- Predictable behaviour for edge cases
- Complex or structured tasks

For instance, if you want the model to generate JSON responses for API errors, showing one correct example before asking for more will make it much more likely to produce accurate results.

In short, examples act like temporary training data for that prompt, guiding the model toward the output you need without retraining it.

---

## Combining How LLMs Work, User And System Prompts, And Examples

Putting that all together, the prompt provides the context or short-term memory that the LLM uses to make predictions. The precise details depend on the model, but generally:

- System prompts shape behaviour.
- User prompts shape the specific task.
- Examples create patterns the model tries to follow.

---

## Prompt Engineering Fundamentals

### Specificity and Clarity

Be specific and clear about what you want. For example you can be more specific when prompting for code generation by:
 - Specifying the programming language, framework and version to use.
 - Defining the scope of the output. Be clear if it's a function, class, module, or whole program.
 - Include requirements and constraint.
 - Avoid ambiguity. Don't use words like 'it' be specific about what 'it' is.
 - Define the desired output format. If you want just code, specifically ask for that "only provide the code".
 - Precise Instructions: Be concise in your input prompts. State your goal clearly without fluff.

### Consistency And Structure

Maintain a uniform structure throughout your prompts and explicitly define ambiguous terms.

### Constraints

Place behavioral constraints and role definitions in the System Instruction or at the very top of the user prompt to ensure they anchor the model's reasoning process.

### Context

Manage the contect effectively. When working with large contexts, place your specific instructions at the end of the prompt.

When transitioning from a large block of data to your query, explicitly bridge the gap. Use a framing phrase like "Based on the information above..." before you define the task to be done.

### Provide Examples (In-Context Learning)

Include concrete input-output examples to show the model exactly what you expect.

Even one example can dramatically improve reliability for structured tasks like generating JSON, SQL, or API responses.

### Stepwise Reasoning

Encourage the model to think step by step for complex tasks. Use phrases like “Explain your reasoning first, then provide the solution” to improve correctness.

This reduces errors in multi-step tasks like debugging, refactoring, or designing systems.

### Iteration and Refinement

Prompt engineering is rarely perfect on the first try.

Break large tasks into smaller prompts or refine based on output.

Use prompt chaining or Tree-of-Thought techniques for multi-step or branching tasks.

---

## Prompt Engineering Techniques

Below are the techniques worth learning first. Each includes a short explanation and a backend or systems programming example.

### Zero Shot

Ask the model to perform a task with no examples.

Useful for simple or common tasks.

Example:
Write a bash script that tails a log file and highlights the word ERROR.

### One Shot, Few Shot, and Multi Shot

Give one or more examples before the task. The model follows the pattern.

Useful when format matters.

Example:
Provide one API error response, then ask for three more in the same format.

### Chain of Thought

Ask the model to show its reasoning steps before giving the final output.

Useful for planning, architecture, debugging, or edge case analysis.

Example:
Walk through the steps you would take to design rate limiting for a distributed API gateway. Explain the reasoning first, then give the design.

### Zero Shot Chain of Thought

Tell the model to think step by step without providing examples.

Useful when you want deliberate reasoning and lower risk.

Example:
Explain step by step how to debug a memory leak in a Go service using pprof.

### Role Prompting

Tell the model who it is or how it should behave.

Useful for consistency and tone.

Example:
You are a senior Rust engineer reviewing a pull request. Highlight security issues, concurrency issues, and API design problems.

### Metaprompting

Write prompts that help the model create better prompts or templates.

Useful when you want reusable patterns.

Example:
Create a reusable prompt that generates idempotent Terraform modules given a resource specification.

### Self Consistency

Ask the model to generate several different answers and choose the best one.

Useful when you want creative or varied reasoning paths.

Example:
Generate three retry strategies for a message queue. Pick the one with the highest safety margin.

### Generated Knowledge

Ask the model to gather facts or brainstorm before solving the task.

Useful when you need domain awareness.

Example:
First list the failure modes of distributed locks. Then design a Redis based lock that handles as many as possible.

### Prompt Chaining

Break a large task into smaller prompts.

Useful for complex generation.

Example:

1. Generate the data model
2. Generate SQL migrations
3. Generate the API handlers
4. Generate the integration tests

### Tree of Thoughts

Ask the model to explore several reasoning branches before deciding.

Useful for architecture and design tradeoffs.

Example:
Explore three architectures for a log ingestion pipeline. Compare throughput, reliability, and operational cost.

### ReAct Prompting

Blend reasoning with tool use.

Useful for agents or tool calling.

Example:
Inspect a Dockerfile, run a linter, then propose improvements based on the output.

---

## Prompting Anti Patterns

Avoid the following:

* Asking for several unrelated tasks in one prompt
* Giving no constraints
* Asking vague questions like improve this code
* Forgetting the output format
* Mixing system rules with task instructions
* Providing no examples when format matters
* Assuming the model knows unshared context
* Using huge prompts instead of breaking tasks into steps

These issues cause most prompt failures.

---

## Conclusion

Prompt engineering is not magic. It is just clear communication. You guide the model with structure, examples, constraints, and roles. You iterate until the output matches what you need.

Start simple. Add detail only when needed. Combine techniques when tasks grow more complex.

If you treat prompts like small specs, you will get better work from any LLM.












# Prompt Engineering

## What Is Prompt Engineering?

## Why Does Prompt Engineering Matter?


## Prompt Engineering Techniques

Note these techniques can be combined in the same prompt.

### Zero-Shot Prompting

### One-Shot, Few-Shot And Multi-Shot Prompting

### Chain-Of-Though Prompting

### Zero-Shot Chain-Of-Though Prompting

### Role Prompting

### Metaprompting


### Self-Consistency


### Generated Knowledge Prompting


### Prompt Chaining


### Tree Of Thoughts

### ReAct Prompting


## Useful References

- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
- Paper: []() Actionable insight:
