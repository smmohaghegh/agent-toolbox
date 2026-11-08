# After release and clean-up

## Verify production changes

For manual changes, verify the intended subject and result using an approved read-only admin interface, audit event, API or database query. Check stable identifiers as well as display names to avoid near-name mistakes. Read only the minimum necessary fields and bound large log queries by time and relevant identifiers.

Record the expected state, observed state, evidence source and verification time. Distinguish verified, failed and not observable. Report unexpected changes without silently repairing them.

## First real use

Record bugs, deferred review points and operational friction as follow-up tasks with problem, evidence, impact, proposed fix and acceptance criteria. Group small changes only when they share scope and review needs.

Do not declare a smoke test passed solely because nobody complained. If relying on owner-confirmed real use, state the observed scenario and the limits of that evidence.

## Operational documentation

Prepare instructions against the released version. Capture screenshots in an approved environment running that version, using safe test data. Align effective dates with actual availability. Apply the team's versioning, acknowledgement and specialist approval policy where one exists.

## Close the work

1. Match each mission's final state to its acceptance and release evidence. Link PRs, deployment and verification.
2. Keep unfinished work open. Use a follow-on epic only when it improves ownership; otherwise retain follow-ups in the existing structure.
3. Close the epic only when its agreed completion criteria are met. Record what shipped and where remaining work lives.
4. Close superseded items with a pointer to the replacement.
5. Assign unresolved chases and communications a durable owner and destination. Do not close them merely because a draft message exists.
6. Finish the release task when its blocking steps have evidence. Keep non-blocking work visible.
7. Save the handover before stopping the agent or environment.

## Lessons

Propose a dated record of the failure, its cause, the preventive check and where that check belongs. Generalise only reproducible lessons. Obtain the relevant authority before updating shared process documents or skill instructions.
