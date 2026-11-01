# How to add a new feature

The flow is `grill-with-docs` → `to-spec` → `to-tickets` → `implement-spec` in a fresh context. Planning stays in one conversation. The human invokes the skills and passes the implementation prompt to the fresh session.

After `to-tickets`, return this prompt with the actual spec and ticket references filled in:

```text
/implement-spec <spec path or URL>
Tickets: <ticket paths or URLs>
```

For Codex CLI or IDE, use `$implement-spec` in the generated prompt.
