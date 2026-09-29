# Draft: a portable skill for adopting SiloZilla

Design sketch for future implementation, not an installed skill or additional project policy. The [project initialization guide](how-to-initialize-project.md) and [feature workflow](how-to-write-specs.md) remain authoritative. Keep this draft out of initialized projects.

## Purpose and boundary

Help an existing project adopt SiloZilla without losing product intent, architectural decisions or useful regression coverage. New products use the initialization guide's [greenfield path](how-to-initialize-project.md#greenfield-new-product). Adoption does not imply a source move, stack replacement, production deployment or conversion of every test to Gherkin.

Proposed package: `skills/adopt-silozilla/SKILL.md`, using the standard frontmatter:

```yaml
---
name: adopt-silozilla
description: Guide an existing repository through staged adoption of SiloZilla, preserving domain knowledge and regression coverage. Use when migrating an existing project's development workflow to SiloZilla.
---
```

## Proposed flow

1. **Discover.** Read the target's instructions and inspect code, tests, branches, context and tracker configuration. Establish the starting revision and verification baseline; separate observed behaviour, approved agreements and unresolved conflicts.
2. **Agree.** Follow the framework's discussion gate for adoption scope, preservation requirements and completion criteria. Reuse settled answers. A conceptual question discovered later returns the affected work to this gate.
3. **Configure.** Reuse installed skills and existing project configuration. Delegate missing configuration to `setup-matt-pocock-skills`; use its selected tracker for the adoption plan and tasks.
4. **Recover knowledge.** Use `domain-modeling` for resolved vocabulary and decisions. Show where useful existing context will live before retiring old material. Inferred behaviour stays provisional until agreed.
5. **Migrate by capability.** Follow the feature workflow for each slice. Track scenario, executable binding and retained/replaced regression coverage in its ticket. Keep structural refactors distinguishable from approved behaviour changes.
6. **Hand over.** Report configured workflow, executable capabilities and remaining work separately. A second invocation resumes from this state instead of recreating configuration or repeating settled discussions.

Delegate interviewing, domain modeling, spec/ticket formats and TDD to the installed Matt Pocock skills. Package or locate the matching SiloZilla guidance when implementing the skill; avoid references that only work inside this draft repository.

## Cross-agent packaging

Use the [Agent Skills standard](https://agentskills.io/specification): plain Markdown and `name`/`description` frontmatter. Keep the body independent of vendor-specific tool names, slash syntax and execution APIs.

- [Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) discovers repository skills under `.agents/skills/` and supports symlinked skill folders.
- [Claude Code](https://code.claude.com/docs/en/skills#choose-where-skills-load) discovers repository skills under `.claude/skills/` and supports symlinked skill folders. Automatic discovery from `.agents/skills/` alone is not documented.
- Keep one skill source; install or link it into each agent's supported discovery location. For example, `.claude/skills/adopt-silozilla` can point to `../../.agents/skills/adopt-silozilla`. Other agents use their own supported locations; format compatibility does not guarantee automatic discovery.
- Verify shared project instructions load too. Claude Code's [AGENTS.md support](https://code.claude.com/docs/en/memory#agentsmd) depends on version and existing Claude instruction files; use a reference/import when needed instead of maintaining duplicate rules.

The installed `grill-with-docs` wrapper composes `grilling` and `domain-modeling`. Use the host's supported invocation mechanism; setup and tracker conventions remain owned by the [upstream skills](https://github.com/mattpocock/skills).

## Checks before releasing the skill

- Claude Code and Codex discover and read the same skill body; additional supported agents are checked explicitly.
- Existing local-Markdown and external-tracker projects retain one maintained set of specs and tickets.
- Missing setup is detected even when skills are already installed; repeated adoption preserves existing configuration.
- Migration waits for agreement, resumes discussion on conceptual conflicts and never labels inferred behaviour as approved.
- A completed first capability remains distinguishable from completed adoption of the whole product.
