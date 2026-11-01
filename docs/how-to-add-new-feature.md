# How to add a new feature

The flow is `grill-with-docs` → `to-spec` → `to-tickets` → handoff → `implement-spec` in a fresh context. Planning stays in one conversation. The human invokes the skills and transfers the handoff to the fresh session.

Follow the repository-specific rules in [how to write specs](how-to-write-specs.md) and [how to write code](how-to-write-code.md). For missing project configuration, follow [project initialization](how-to-initialize-project.md). Each skill owns its workflow.

Once the spec and tickets are ready, read the installed `handoff` skill's instructions and prepare the handoff accordingly, with `implement-spec` as the sole suggested skill.

Return the handoff's absolute path and the following prompt with that path filled in, then wait for the human to transfer it:

```text
/implement-spec
Read <absolute handoff path>.
```

For Codex CLI or IDE, use `$implement-spec` in the generated prompt.
