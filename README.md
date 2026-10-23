# improve-prompts

vibe coded claude skill based on x post for prompt that improves your prompts before they're executed.

A small Claude skill that clarifies a task once before execution. Clear requests pass through unchanged. Refinement uses no tools or subagents, aims for fewer than 80 words, and preserves essential constraints.

## Install

Copy the `.claude/skills/improve-prompt` directory from this repository into your project's root, preserving the `.claude` directory, then commit `.claude/skills/improve-prompt/SKILL.md`.

The only required skill file is `.claude/skills/improve-prompt/SKILL.md`. There are no dependencies, scripts, API keys, or external services.

Open the repository in Claude Code and invoke:

```text
/improve-prompt Create an authorization-testing skill from these writeups.
```

To inspect a rewritten prompt without executing it:

```text
/improve-prompt rewrite-only: Create an authorization-testing skill from these writeups.
```

For availability across local projects, copy the improve-prompt directory to `~/.claude/skills/` instead.

## Behavior

- Resolve ambiguity using existing conversation context.
- Ask one concise question when missing details materially change the work.
- Preserve scope, output requirements, exact literals, and authorization boundaries.
- Execute without displaying the rewrite unless requested.
- Return only the prompt when rewrite-only or prompt editing is requested.

Explicit invocation selects the skill. This package does not install an automatic before-every-message hook. Actual token savings require measurement; loading the skill itself adds overhead.

## Origin

Inspired by Felix Rieseberg's article, adapted for minimal clarification overhead:
https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/
