# AGENTS.md

Behavioral guidelines for Codex and other coding agents working in this repo. Merge these with task-specific user instructions.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Do not assume. Do not hide confusion. Surface tradeoffs.**

Before implementing:
- State assumptions explicitly when they affect the implementation.
- If multiple interpretations exist, present them instead of silently choosing one.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear enough to make implementation risky, stop, name the ambiguity, and ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- Do not add features beyond what was asked.
- Do not add abstractions for single-use code.
- Do not add flexibility or configurability that was not requested.
- Do not add error handling for impossible scenarios.
- If a solution is much larger than the problem warrants, simplify it before finishing.

Ask: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own changes.**

When editing existing code:
- Do not improve adjacent code, comments, or formatting unless needed for the task.
- Do not refactor things that are not part of the requested change.
- Match existing style, even if you would normally choose a different style.
- If you notice unrelated dead code, mention it instead of deleting it.

When your changes create orphans:
- Remove imports, variables, functions, and files that your changes made unused.
- Do not remove pre-existing dead code unless asked.

The test: every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" -> "Write tests for invalid inputs, then make them pass."
- "Fix the bug" -> "Write a test that reproduces it, then make it pass."
- "Refactor X" -> "Ensure tests pass before and after."

For multi-step tasks, state a brief plan:

```text
1. [Step] -> verify: [check]
2. [Step] -> verify: [check]
3. [Step] -> verify: [check]
```

Strong success criteria allow independent progress. Weak criteria such as "make it work" require clarification.

## 5. Attribution

Do not add `Co-Authored-By`, Claude-related, or Codex-related footers unless the user explicitly asks.

## 6. Commit Messages

When creating commits, match the style of recent commits in this repository. Prefer the existing conventional prefix pattern, such as `chore:`, `fix:`, `feat:`, or scoped forms like `chore(data):`, and use Korean summaries when that is the surrounding style.
