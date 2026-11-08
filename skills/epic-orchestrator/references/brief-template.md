# Brief template

Prepare one bounded brief per mission or review fix. Verify repository paths, branch states and dependencies before showing it to the owner.

```text
# <Task reference>: <one-line outcome>

Outcome
<What the user will be able to do and why.>

Authority
Implement within this brief using full access to the dedicated development VM.
Run and deploy the development stack, test, inspect and fix repeatedly until
the acceptance criteria are met. Open PRs; do not merge or deploy to production.
<VM identity, full development permissions, standing authorisation and boundaries.>
Routine development iterations within this mission need no further approval.

Background
<Evidence, tracker links, related PRs and their observed states.>

Repository and base
<Repository, base branch and dependencies.>
Before every push, check the PR is open and still targets the intended branch.
If a parent merged or the PR closed, stop pushing to that PR and establish
a correct current base and a new PR where required.

Scope
<Included changes.>
<Excluded behaviour, interfaces, data and files.>

Build
1. <Concrete change and relevant paths.>
2. <Additional bounded change.>

Acceptance and tests
<Observable acceptance criteria, regression cases, integration tests and
necessary security/accessibility/domain checks.>
Report what actually ran, its result and the tested commit.
Explain skipped checks and remaining uncertainty.

Iteration and completion
Implement, run the full stack, exercise the acceptance scenarios, inspect failures
and fix code or the VM environment. Repeat until the evidence proves the goal.
Re-run affected regressions after fixes. Keep a checkpoint after each cycle.
If blocked, record the attempted fixes, evidence and smallest decision needed;
continue independent work. Do not weaken tests or acceptance criteria to finish.

Compatibility and release
<Schema/configuration/content dependencies; required order; feature flags;
migration responsibility; documentation timing.>
Do not perform production changes under this implementation brief.

PRs
<Expected PRs, targets, links and reviewer roles.>
Include outcome, scope, validation evidence, release dependencies and
Questions for the owner. Do not guess on blocking decisions.

Handover
Update the durable progress record. Report PR links, tested commit,
blockers, decisions and remaining work. Wait when authority is exhausted.
```

## Before dispatch

- Check shared helpers, types, schemas and all known consumers for blast radius.
- Prefer the established data model over new hard-coded identifiers.
- Watch for repeated queries, unbounded work and unsafe migration assumptions.
- Specify test data and environments; never include real secrets or customer records.
- Separate documentation or content PRs only when timing, ownership or approval needs justify it.
- Show the exact dispatch text unless existing authorisation already covers it.
