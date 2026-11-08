# Full-access VM build agent

## Operating model

Run the agent inside a dedicated development VM with the full application stack. The VM gives the agent enough control to make progress without asking a human to run ordinary development commands. The cloud provider, VM size, coding agent and connection mechanism are project choices; this architecture is the core of the workflow.

Provision full development access within the VM:

- Read and write the working repositories, create branches, commit and push approved work, and open PRs.
- Run arbitrary development shell commands and install dependencies and tools.
- Use sudo/root where needed and authorised to configure and repair the VM.
- Start, stop, rebuild, configure and inspect development services and containers.
- Query, reset, seed and migrate development databases using approved test data.
- Run the application, background workers and integrations required for representative tests.
- Use a browser, take screenshots, inspect logs and network behaviour, and run unit, integration and end-to-end tests.
- Persist progress, recover from interrupted runs and continue the mission.

Configure the agent's supported permission mode to cover these authorised development actions. Verify the actual capabilities before launch. Full access is confined to the dedicated development VM and the agreed repository workflow. It does not imply production credentials, merge authority or access to unrelated infrastructure. Respect host-enforced controls; if required access cannot be granted, make the gap explicit.

## Pre-flight

Use the team's current operations runbook for exact commands. Confirm:

1. VM identity, connection, agent session and the approved goal and scope.
2. Full development access, including needed administrative operations and credentials for repository pushes and test dependencies, without printing secrets.
3. The complete stack is healthy and reachable, with representative safe test data and required test integrations or documented substitutes.
4. Disk, memory and build concurrency are sufficient for repeated builds and tests.
5. Intended checkouts, base branches, inputs and dependencies are current. Inspect local work before pulling or changing branches.
6. Acceptance scenarios can actually be exercised and observed through a browser, API, database or other relevant interface.
7. Durable state and session supervision are ready; there is no overlapping writer or duplicate mission.

If a dependency must be simulated, document which part of the outcome remains unverified. Do not describe a stubbed integration as a verified real integration.

## The repeat-until-done loop

Once the owner approves the mission, execute this loop without requesting a new approval for each routine development step:

1. Read the brief and current durable state. Turn the agreed goal into observable acceptance checks.
2. Inspect and implement the next bounded change.
3. Build and run the real development stack in the VM. Perform any in-scope environment repair required to make it run.
4. Exercise the actual acceptance scenarios, including the user journey and affected integrations. Run relevant regressions.
5. Inspect failing assertions, browser behaviour, logs, service state and development data. Identify the cause and fix the code, configuration or environment.
6. Repeat the affected checks after each fix. Keep broader regression evidence current as the change grows.
7. Checkpoint the tested commit, results, failures, attempted fixes and next action. Continue until every agreed acceptance criterion has evidence.
8. Open or update the PR with the actual evidence and outstanding limitations. Recheck PR state before every push. Finish with a handover suitable for human review.

Do not stop merely because code was written, a PR was opened or unit tests passed. Do not change acceptance criteria, delete failing tests, hide failures or fabricate evidence to declare success. A verified development outcome is ready for human review; production verification remains a separate release stage.

If repeated attempts stop producing new evidence or progress, diagnose the blocker instead of repeating the same failing action. Record the attempts and smallest required intervention, then continue independent authorised work. Pause only the affected work for missing external access, a human decision, exhausted agreed resource limits or an out-of-scope action. Do not turn an arbitrary iteration count into a substitute for achieving the goal.

## Durable state and long runs

| File | Purpose |
|---|---|
| RUN.md | Approved goal, scope, VM permissions, mission order and standing rules |
| PROGRESS.md | Acceptance checks, current state, PRs, tested commit and next action |
| BLOCKED.md | Evidence, attempted fixes, affected sub-items and smallest external intervention |
| DECISIONS.md | Decisions, rationale, authority and reversible development defaults |
| SUMMARY.md | Final evidence, tests, limitations and handover |

Use a supported persistent session and process supervisor where available. Distinguish a finished agent from one that crashed, is waiting or is disconnected. Save checkpoints before a context reset, then reload the brief and durable state to resume. Never claim continuous monitoring unless a real monitoring mechanism is running.

## Brief delivery and supervision

1. Write the complete brief to a durable file on the VM.
2. Show the owner the exact brief and obtain mission-level approval unless standing authority already covers it.
3. Send a short prompt pointing to that file through the verified agent interface.
4. Confirm receipt in observed output and record the brief version.
5. Inspect progress, acceptance evidence, session health, PRs and CI. Give new scope or decisions through an approved updated brief; ordinary iterations remain covered by the original mission.

## VM lifecycle and recovery

Use the project's operations runbook to create, start, stop, snapshot or delete the VM. Act within existing authority; obtain missing authority for chargeable or destructive actions. Preserve uncommitted work and unpushed branches before shutdown or deletion. Do not treat a snapshot as proof of a tested restore.

After creation, restart or restoration, check services, repositories, development data and resource headroom before trusting test results. Keep connection details and infrastructure identifiers in private project records.

| Interruption | Response |
|---|---|
| Agent exited or stopped reporting | Inspect process state, logs and checkpoint; resume or restart within mission authority |
| Memory or disk exhaustion | Repair within agreed resources, bound concurrency and preserve work |
| Development service or dependency fails | Diagnose and repair in the VM, then rerun the affected checks |
| Required permission is missing | Identify and request the specific missing capability; do not silently downgrade the workflow |
| Parent PR merged during work | Reconcile against the actual target state and merge strategy before another push |
| Context is no longer reliable | Checkpoint, reset between tasks and reload durable state |
| Duplicate tracker items | Reconcile the existing records and assign tracker ownership |

Use precise process or service identity for supervision so monitoring commands cannot be mistaken for the agent itself.
