# Shared product, development and QA workspace

![SiloZilla: a cheerful Godzilla stomping silos labelled Product, Dev, and QA](assets/silozilla.png)

A thin framework over [Matt Pocock Skills](https://github.com/mattpocock/skills) that keeps product owners, developers and QA aligned through shared domain language and approved `.feature` scenarios. Scenarios become executable E2E specifications; code and ADRs preserve implementation and architectural decisions. This template adds collaboration and simplicity rules to the skills' engineering workflows.

**Dependencies:** Git, `tree`, an agent supporting Matt Pocock Skills, and the engineering skills used by this framework. Node.js/npm is needed for the installer below; the application stack and scenario runner are chosen per project.

## How it works

Product, development and QA often keep separate descriptions of the same feature. Intent gets lost in handoffs, domain terms drift, and tests can end up checking something different from what the product owner meant. SiloZilla gives all three roles one shared workspace: a common domain language and approved `.feature` files that preserve both the intent and the examples of expected behaviour.

```mermaid
flowchart TD
    P["Product owner + agent: clarify intent and examples"]
    S["Approved .feature files: shared executable specification"]
    D["Developer + agent: agree architecture and plan the work"]
    T["Development: bind scenarios to E2E tests and implement with TDD"]
    Q["QA: verify behaviour and explore missing cases"]
    P --> S --> D --> T --> Q
    S -. "same scenarios" .-> Q
    D -. "unclear or changed behaviour" .-> P
    Q -. "missing or ambiguous cases" .-> P
```

1. **Agree the behaviour.** The agent grills the product owner about who needs the feature, why, its scope and concrete examples. Capture shared terms through domain modeling and get the owner's approval of the `.feature` scenarios.
2. **Plan the implementation.** Grill the developer against those scenarios: architecture, testable public interfaces and task breakdown. After both discussions, use `to-spec` for the temporary Markdown plan and `to-tickets` for tasks linked to the approved scenarios. Review before publishing.
3. **Make the agreement executable.** Use `tdd` to connect scenarios to the product through step bindings, then implement until the E2E tests pass. Tests exercise observable product behaviour through UI, CLI or external API. Unit tests need explicit user approval for their scope.
4. **Verify and refine.** QA reads the original intent and runs the same scenarios, then explores gaps. Missing, ambiguous or changed behaviour goes back to the product owner for agreement before scenarios change.

The lasting specification stays in `features/<capability>/<slug>.feature`, versioned with the code. Feature descriptions preserve the product intent, `CONTEXT.md` preserves domain vocabulary, and ADRs preserve qualifying architectural decisions. Before temporary plans or tickets are deleted at feature merge, check that this lasting context is complete.

## Getting started

Ask your agent to follow [the project initialization guide](docs/how-to-initialize-project.md) for a new or existing project.

## Sources and acknowledgements

- [Matt Pocock Skills](https://github.com/mattpocock/skills) supplies the engineering workflows this framework builds on
- [FerroxLabs/agents-md](https://github.com/FerroxLabs/agents-md) containing valuable instructions, copyright Sean Donahoe
- [Karpathy-inspired coding guidelines](https://github.com/multica-ai/andrej-karpathy-skills), for simplicity and surgical-changes rules
- [Rinat Abdullin’s materials](https://abdullin.com/) are the source of the `AICODE-` convention, executable specs and many others the repo

