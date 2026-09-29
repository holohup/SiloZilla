# How to write code

The minimum code that solves the stated problem, changed in the smallest reviewable diff.

## Simplicity first

- No features beyond what was asked. No abstractions for single-use code; no configurability, flexibility or hooks nobody requested. "For future extensibility" is a future decision.
- No error handling for impossible scenarios. Handle the failures that can actually happen.
- Bias toward deleting code over adding it.
- Follow existing code patterns and style, even where you would choose differently in a new project.
- Names must be self-explanatory; a comment is justified only by what code cannot express: an external quirk being worked around, a non-obvious invariant, a rejected obvious approach. Never ticket tags, dates or plan narratives in comments - that history lives in git and the ticket. This overrides "match existing style": legacy code dense with narrative comments is not a pattern to imitate. AICODE- anchors follow the same bar.
- For searchable inline knowledge, use `AICODE-NOTE:`, `AICODE-TODO:` or `AICODE-QUESTION:` as appropriate. Before scanning files, search for existing `AICODE-` anchors; update relevant anchors when finishing the task.

## Testing

Design the architecture to support the product E2E scenarios.

Add unit tests only where needed, such as for complex algorithms or method edge cases. Before writing them, explain why they are needed, identify the interface and specific cases to test, and obtain the user's explicit approval. Approval covers that scope; obtain further approval before expanding it.

## Surgical changes

- Every changed line traces directly to the request. If a line fails that test, revert it.
- Do not improve, reformat or refactor adjacent code because you are in the file. Do not delete pre-existing dead code unless asked; mention it in the summary.
- Do clean up orphans your own change created: unused imports, variables, functions.

## Before saying done

- Run it. Tests, linter, type checker - whatever exists. A plausible-looking diff is not correctness.
- Read the whole error, log or stack trace. Half-read traces produce wrong fixes.
- Diagnose verification failures. Fix faulty code or checks without weakening approved behaviour.
