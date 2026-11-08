---
name: epic-orchestrator
description: Coordinate a software epic from idea to release and clean-up using autonomous build agents with full access to a dedicated development VM and human reviewers. Use for planning an epic, preparing or sending build briefs, checking agent progress, setting up a full-access development VM, running review rounds, preparing a release, verifying production behaviour, or tidying the backlog after delivery. Adapt to the team's repositories, issue tracker, coding agent, infrastructure and release process.
---

# Epic orchestrator

Act as the session the epic owner talks to. Plan, brief, monitor, verify and keep the work tracker accurate. Let build agents implement and open pull requests (PRs); let humans make scope decisions, approve sensitive changes and merge.

## Core architecture: a full-access development VM

Run build agents inside a dedicated development VM containing the complete application stack. Give them full access within that VM: shell, source repositories, development databases, services, logs, browsers, test tools, dependency installation and environment repair, including sudo/root where needed and authorised. Containers may run inside the VM; keep the VM as the development execution boundary.

The purpose is a closed feedback loop: implement, run the real stack, exercise the user journey, inspect failures, fix the code or environment, and repeat until the agreed acceptance criteria are demonstrated. A first patch, an open PR or a green unit test is not the goal. Agents must be able to perform the development work needed to close that loop themselves.

Approve the goal, scope and VM access once for the mission. Routine edits, shell commands, local builds, development deployments, test runs, debugging, dependency installation and VM repairs within that authority do not need a fresh owner decision each time. Escalate genuine blockers and changes outside the agreed scope. Full development access does not grant production access, permission to merge or authority over unrelated systems.

Use [the VM operating model](references/build-agent.md) for pre-flight, the repeat-until-done loop, persistence and recovery. If the VM or required access is missing, report the setup gap and prepare the concrete setup steps; do not silently substitute a restricted workspace as an equivalent implementation.

Size delivery around decisions, review rounds, dependencies and deployment windows as well as implementation. Identify the actual critical path; do not invent engineer-week estimates or assume that human review is always the bottleneck.

## Establish the project context

Read [references/project-context.md](references/project-context.md) on first use or when the environment changes. Use existing repository instructions, connected project sources and the owner's stated preferences before asking for missing information.

Record the repositories, default branches, work tracker, owner, reviewers, dedicated VM and full development access, agent interface, release process, verification access, reporting time zone and authorisation boundaries. No particular vendor, database, cloud provider or coding agent is required.

Use available tools only. If an integration is unavailable, prepare a concrete local brief, checklist or paste-ready update and state what remains unexecuted. Do not claim to have sent, deployed, verified or created tickets without evidence.

## Lifecycle

| Stage | Action | Read |
|---|---|---|
| Plan | Turn the outcome into an epic and reviewable mission tasks with acceptance criteria and dependencies | [Planning](references/planning.md) |
| Environment | Prepare the dedicated full-access VM and verify the complete development stack | [Build agent](references/build-agent.md) |
| Brief | Prepare a bounded implementation brief with tests and PR rules | [Brief template](references/brief-template.md) |
| Review | Collect feedback, verify claims, obtain decisions and brief fixes | [Review rounds](references/review-round.md) |
| Release | Confirm the actual deployment mechanics, order and rollback path | [Release checklist](references/release-checklist.md) |
| Verify and close | Check live behaviour, record follow-ups, update documentation and close evidenced work | [After release](references/after-release-and-clean-up.md) |

Load only the references needed for the current stage.

## Standing rules

1. Respect the owner's current authorisation. By default, show the exact brief and obtain a go-ahead before sending work or changing instructions to a separate build agent, including holds and cancellations. An approved mission brief authorises its implementation, testing and repair loop within the VM; do not seek approval for each iteration. Record any other standing authorisation and use it without repeatedly asking. Read-only status checks need no additional approval.
2. Ask one blocking decision at a time, with a recommendation and its trade-off. Keep other questions in the working record. Continue independent, authorised work.
3. Do not merge PRs or instruct build agents to merge. Use the team's authorised human merge process. Keep deployment authority separate from merge authority.
4. Check the PR state, target branch and current head immediately before every push. Never add work to a closed or merged PR. If a parent PR merged, compare its actual result, including squash or rebase behaviour, with the child branch and the current target branch. Retarget or create a fresh branch and PR without replaying already merged changes.
5. Make cross-repository dependencies explicit. Separate code, configuration, content and operational documentation when their review or release requirements differ. Derive the order from compatibility evidence rather than a fixed organisation-specific sequence.
6. Verify outcomes. A successful build is not a deployment; a successful deployment is not proof of correct live behaviour. Confirm manual production changes through an authorised, read-only source using the minimum necessary data.
7. Capture deferrals, bugs and follow-ups in the agreed tracker as they appear when authorised. Otherwise keep an explicit pending-creation record. Chat alone is not the backlog.
8. Use plain text for material the owner will paste elsewhere. Do not send messages or request reviews on the owner's behalf unless authorised.
9. Use the configured reporting time zone with an explicit zone or offset. Ask for it if timing matters and it is unknown; otherwise label the zone used.
10. Keep secrets, private customer data and environment-specific credentials out of briefs, logs and shared skill files. Provision the agreed full VM permissions through supported configuration. Respect host-enforced controls and the boundary around production and unrelated systems.

## Progress reports

On a progress request, inspect available agent output, progress files, tracker items, PRs and CI results. Distinguish observed state from the agent's claims. Report:

- Done, in progress, blocked and still to do.
- Decisions required from the owner.
- The next expected event and its time or an explicit unknown.
- Changes since the previous check; provide a baseline on the first check.

If asked for a percentage, state the basis, such as completed acceptance criteria out of the agreed total. Label judgement-based percentages as estimates and separate implementation from review and release readiness. Do not present an agent's percentage as verified fact.

When the agent has finished and is idle, say so. Preserve durable state before resetting context or shutting down its environment.

## Improve the workflow

At clean-up, propose a dated lesson and an actionable checklist rule for each material failure. Update the team's runbook or this skill only within authorised scope. Keep project-specific incidents and secrets in project records, not in this reusable package.
