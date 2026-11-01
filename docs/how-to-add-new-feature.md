# How to add a new feature

You invoke each skill yourself. The examples use slash syntax; in Codex CLI or IDE, select the skill through `/skills` or use `$skill-name`.

For an unconfigured project, follow [project initialization](how-to-initialize-project.md) first. This repository's additions to the skill workflows live in [how to write specs](how-to-write-specs.md) and [how to write code](how-to-write-code.md).

## 1. Plan in one conversation

Invoke these one at a time in the same conversation:

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

In the planning conversation, submit:

```text
/handoff
The next session will use implement-spec to implement <spec path or URL>.
Suggested skills: implement-spec only.
```

## 3. Open a fresh session

Open a new agent session yourself in the same repository with a clean context. Give it this prompt using the handoff path returned above:

```text
/implement-spec
Read <absolute handoff path>.
```
