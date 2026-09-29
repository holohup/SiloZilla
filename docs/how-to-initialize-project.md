# How to initialize a project

## Inspect and agree

Inspect the target's instructions, code, tests and existing skill configuration. Choose the applicable path below and agree the scope and completion criteria before making changes. Reuse decisions already agreed with the user.

### Greenfield: new product

Agree the product purpose, stack, layout, scenario runner and base branch for changes and PRs.

### Brownfield: existing product

Agree a staged adoption plan and confirm the base branch for changes and PRs. Retain the stack, layout and regressions unless their changes are agreed. A move into `src/` is a separate migration decision, not a framework requirement.

Distinguish observed behaviour from approved requirements; bring conflicts to the user. Adopt executable scenarios one capability at a time, preserving distinct regression coverage and context before retiring old material.

## Apply the agreed setup

1. Initialize Git if needed. Ensure Matt Pocock Skills is installed for the participating agents and configured for this repository using the [upstream instructions](https://github.com/mattpocock/skills). Reuse existing installation and configuration; installed skills alone do not mean the repository is configured.
2. Merge SiloZilla's `AGENTS.md` guidance and instruction guides into the target, preserving project-specific material. Ensure each participating agent loads the shared instructions.
3. Fill `about-project.md` with the agreed project settings and verified commands.

## Verify setup

Verify agent discovery, project configuration and the commands that are available. Report separately what is configured, what behaviour has executable coverage, and what remains to migrate; completed setup does not imply completed behaviour migration.
