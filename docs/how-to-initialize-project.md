# How to initialize a project

1. Inspect the target's instructions, code, tests and existing skill configuration. Choose **greenfield** for a new product or **brownfield** for an existing one. Reuse decisions already agreed with the user.
2. Ensure Matt Pocock Skills is installed for the participating agents and configured for this repository using the [upstream instructions](https://github.com/mattpocock/skills). Reuse existing installation and configuration; installed skills alone do not mean the repository is configured.
3. Merge SiloZilla's `AGENTS.md` guidance and instruction guides into the target, preserving project-specific material. Initialize Git if needed. Ensure each participating agent loads the shared instructions.

## Greenfield: new product

Agree the product purpose, stack, layout and scenario runner; fill `about-project.md` with those decisions and actual commands.

## Brownfield: existing product

Agree a staged adoption plan. Retain the stack, layout and regressions unless their changes are agreed. A move into `src/` is a separate migration decision, not a framework requirement. Fill `about-project.md` with the existing stack, runner and verified commands.

Distinguish observed behaviour from approved requirements; bring conflicts to the user. Adopt executable scenarios one capability at a time, preserving distinct regression coverage and context before retiring old material.

## Verify setup

Verify agent discovery, project configuration and the commands that are available. Report separately what is configured, what behaviour has executable coverage, and what remains to migrate; completed setup does not imply completed behaviour migration.
