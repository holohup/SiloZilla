# How to initialize a project

1. Inspect the target's instructions, code, tests and existing skill configuration. Choose **greenfield** for a new product or **brownfield** for an existing one. Follow the [discussion and approval workflow](how-to-write-specs.md) before implementing setup or migration; reuse decisions already agreed with the user.
2. Check which required Matt Pocock skills the active agent can actually discover. Reuse installed skills; install only missing ones using the [upstream instructions](https://github.com/mattpocock/skills#installation-30-second-setup):

   ```sh
   npx skills@latest add mattpocock/skills
   ```

   Select the skills referenced by this framework, including `setup-matt-pocock-skills`, and the agents that will use them.
3. Merge SiloZilla's `AGENTS.md` guidance and instruction guides into the target, preserving project-specific material and excluding design drafts. Initialize Git if needed, following [about-project.md](about-project.md). Ensure each participating agent loads the shared instructions.
4. **Installed skills do not mean this repository is configured.** Inspect the project's tracker and domain configuration. If absent, run `setup-matt-pocock-skills`; otherwise reuse it. Let that skill own configuration structure and tracker selection, including local Markdown or an external tracker. Resolve missing or conflicting choices before producing specs or tickets, then follow the relevant path below.

## Greenfield: new product

Agree the product purpose, stack, layout and scenario runner; fill [about-project.md](about-project.md) with those decisions and actual commands. Begin product work through the [feature workflow](how-to-write-specs.md).

## Brownfield: existing product

Inspect branches, current behaviour, tests, documentation and configured tracker before proposing changes. Agree a staged adoption plan through the discussion workflow above. Merge SiloZilla guidance into existing instructions; retain the stack, layout and regressions unless their changes are agreed. A move into `src/` is a separate migration decision, not a framework requirement. Fill `about-project.md` with the existing stack, runner and verified commands.

Use `domain-modeling` to recover resolved terminology and decisions. Distinguish observed behaviour from approved requirements; bring conflicts to the user. Adopt executable scenarios one capability at a time, preserving distinct regression coverage and context before retiring old material. The [migration-skill draft](draft-adopt-silozilla-skill.md) sketches future automation of this path.

## Verify setup

Verify agent discovery, project configuration and the commands that are available. Report separately what is configured, what behaviour has executable coverage, and what remains to migrate; completed setup does not imply completed behaviour migration.
