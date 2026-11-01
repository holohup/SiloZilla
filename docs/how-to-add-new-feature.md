# How to add a new feature

This guide is for the human running the workflow. The examples use slash syntax; in Codex CLI or IDE, select the skill through `/skills` or use `$skill-name`.

For an unconfigured project, follow [project initialization](how-to-initialize-project.md) first. This repository's additions to the skill workflows live in [how to write specs](how-to-write-specs.md) and [how to write code](how-to-write-code.md).

## 1. Plan in one conversation

The human invokes these one at a time in the same conversation:

```text
/grill-with-docs <feature idea>
```

```text
/to-spec
```

```text
/to-tickets <spec path or URL>
```

## 2. Generate the handoff

The human submits this in the planning conversation:

```text
/handoff
The next session will use implement-spec to implement <spec path or URL>.
Suggested skills: implement-spec only.
```

The planning agent writes the handoff. The human keeps its path before leaving or clearing the conversation.

## 3. Human opens a fresh session and passes the handoff

The human opens a fresh session in the same repository and pastes this prompt, replacing the placeholder with the saved handoff path:

```text
/implement-spec
Read <absolute handoff path>.
```
