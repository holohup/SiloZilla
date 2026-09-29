# How to write specs

Product, development and QA share executable behaviour agreements in `features/<capability>/<slug>.feature`, with one `Feature:` per facet of a capability. Write them so readers can understand the behaviour without seeing the code.

## Workflow

Describe and agree the scope and completion criteria of migrations and other project/process changes via `grill-with-docs` (`grilling` + `domain-modeling`) before implementation. Pause affected work and resume grilling when conceptual questions arise.

1. Grill the product owner using `domain-modeling`. Write the agreed intent and examples as `.feature` files and obtain the product owner's approval.
2. Grill the developer against the approved features: architecture, testing interfaces, task breakdown and implementation details as needed. Unit-test proposals follow `docs/how-to-write-code.md`.
3. Run `to-spec` after both discussions, using its normal Markdown format. This is a temporary planning snapshot; approved `.feature` files remain authoritative for product behaviour.
4. Run `to-tickets`. Both skills use the tracker configured at project setup.
5. Use `tdd` to connect approved scenarios to the product through step bindings and implement the behaviour. QA verifies the same scenarios and looks for missing cases.

For violations of approved scenarios, record reproduction steps and scenario links in a bug ticket; fix with `tdd` and have QA verify, without reapproving behaviour. Missing, ambiguous or changed requirements go to the product owner; update scenarios after agreement.

## Specs and tickets

Follow the installed skills and configured tracker for document structure and storage. Keep one maintained copy of specs and tickets in that tracker; link to it elsewhere. Plans and tickets may precede detailed scenarios; before implementing product behaviour, link the approved `.feature` files and relevant scenarios as ticket acceptance criteria. Link them from the Markdown spec too. For behaviour-preserving refactors, follow `to-tickets` without requiring new scenarios.

Show specs and tickets to the user before publishing and obtain approval. Ticket publication does not create or rewrite behaviour. When reading a ticket, also read every `.feature` file it links.

At feature merge, before the user deletes temporary specs and tickets, verify that feature descriptions preserve the agreed product intent and ADRs capture decisions meeting the `domain-modeling` skill's criteria. Preserve any missing context before cleanup.

## Shape

- The `Feature:` description preserves the agreed product intent: who needs the capability, why, and any scope that the scenarios do not make clear.
- The title is the sentence: `Scenario: The run hands back the best selection, not the last one`. A title that needs the body to be understood is wrong. Folder and file names carry the same weight: `tree features` must tell an agent what exists without opening a file.
- Given / When / Then in `CONTEXT.md` vocabulary. One name per concept, so one grep finds every use.
- Rule-shaped behaviour is one `Scenario Outline` with an `Examples` table, never five prose scenarios. An edge case is another row.
- A scenario reads alone. No `Background`; repeat the given.
- Executes end to end through the product's public entry points: UI, CLI, or external API. Treat the code as a black box. Scenarios and their step bindings must not inspect internal code, query internal storage, or depend on internal collaborators.
- Include file formats, protocol details, timestamps, or identifiers when they are part of the agreed observable contract. Prefer domain language; name a technical detail explicitly when that detail is itself a requirement.

## May not contain

- An internal implementation detail, such as a library choice or storage layout.
- An implementation decision. Those go in the temporary Markdown spec (`to-spec`) or an ADR.
