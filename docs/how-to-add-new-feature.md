# How to add a new feature

Use one planning conversation for `/grill-with-docs` → `/to-spec` → `/to-tickets`, then hand implementation to an agent with a clean context. Run each stage after the previous one is agreed.

These workflow entry points, including `handoff` and `implement-spec`, declare `disable-model-invocation: true` in their installed skills. Invoke each yourself; a suggestion inside a handoff is not an invocation. The examples below use slash syntax. In Codex CLI or IDE, select the skill through `/skills` or mention it as `$skill-name` instead.

Before starting, follow [project initialization](how-to-initialize-project.md) if the project is not configured. The planning and implementation agents need the skills and the repository's tracker configuration; run `/setup-matt-pocock-skills` if that configuration is missing.

## 1. Agree the feature with grill-with-docs

```text
/grill-with-docs
Help me design <feature>. Follow docs/how-to-write-specs.md for the product-owner and developer discussions.
```

Finish with agreed behaviour, scope, implementation decisions and testing seams. Follow [how to write specs](how-to-write-specs.md) for scenario ownership and approval, and [how to write code](how-to-write-code.md) for any unit-test approval. Record those approvals where the next agent can find them.

`grill-with-docs` already combines `grilling` and `domain-modeling`, including glossary updates and ADRs when warranted.

## 2. Capture the agreement with to-spec

```text
/to-spec
Synthesize the agreed feature. Link the approved scenarios using docs/how-to-write-specs.md. Show me the complete draft for approval before publishing.
```

`to-spec` synthesizes the conversation rather than conducting another interview; it includes confirmation of the testing seams. Resolve open design questions in the grilling stage before proceeding. Keep the resulting spec in the configured tracker and retain its path or URL for the next stage.

## 3. Break the spec into tickets with to-tickets

```text
/to-tickets <spec path or URL>
Link the relevant approved scenarios as each ticket's acceptance criteria, following docs/how-to-write-specs.md. Show me the complete ticket drafts before publishing.
```

The skill handles vertical slices, blocking relationships, breakdown approval and publication. Finish with published, approved tickets associated with the spec, each small enough for a fresh context window. Keep the spec and tickets in their configured tracker; reference them elsewhere.

## 4. Generate the implementation handoff

In the planning conversation, use this prompt after the spec and tickets are ready:

```text
/handoff
The next session will implement the agreed feature using implement-spec.

Include the absolute repository path and context pointers to the published spec, its tickets, the tracker configuration, relevant approved scenarios, and any glossary or ADR decisions needed for this feature.

Preserve decisions and user approvals that exist only in this conversation, especially the agreed testing seams, any approved unit-test scope, and permissions already granted for pushing or opening a PR. Distinguish unresolved questions from settled decisions. Include the agreed base branch and verified starting commit for the final review, and any existing implementation branch or work to resume.

In Suggested skills, identify implement-spec as the skill the user must explicitly invoke in the fresh session. Its delegated skills remain its responsibility.

Return the handoff's absolute path and flag anything still missing for implementation.
```

Resolve implementation blockers before starting the new agent. The handoff should carry context that would otherwise be lost, with pointers to the maintained artifacts.

## 5. Start an agent with a clean context

Start a fresh agent in the repository and explicitly invoke the skill with this prompt, replacing the placeholder with the path returned above. In Codex CLI or IDE, use `$implement-spec` on the first line.

```text
/implement-spec
Read <absolute handoff path> and implement the linked spec and its associated tickets. Follow the repository instructions and the decisions and approvals referenced in the handoff.
```

`implement-spec` owns implementation orchestration and already delegates to `tdd` and `code-review`; keep their instructions in those skills. `handoff` already saves outside the repo and references existing artifacts instead of copying them. Repository approval rules still apply; handing off implementation does not grant new permissions.
