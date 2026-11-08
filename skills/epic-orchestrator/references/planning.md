# Plan the epic

1. Define the user outcome, acceptance criteria, exclusions, constraints and evidence of success.
2. Find existing initiatives, epics and tasks before creating new ones. Map to the team's tracker hierarchy rather than inventing project keys or statuses.
3. Split into missions small enough for a focused human review, normally one coherent PR each. Separate repositories or approval domains where necessary.
4. Give each mission an owner, reviewer, acceptance criteria, test approach, dependency links and expected deliverable.
5. Record release and migration dependencies, including compatibility during mixed-version operation.
6. Ensure the dedicated VM can run the complete stack and that the agent has the access needed to iterate through implementation, real-stack testing and repair without per-command hand-offs.
7. Identify decisions, reviewer availability, external approvals and deploy windows on the critical path. Label schedule assumptions and estimates.
8. Prepare the first brief using references/brief-template.md. Obtain approval to dispatch it unless existing authorisation covers it.

## Mission template

- Title and tracker reference:
- User outcome:
- In scope:
- Out of scope:
- Repository and base branch:
- Dependencies and blocking decisions:
- Implementation owner and human reviewer:
- Acceptance criteria:
- Validation evidence:
- PR and release dependencies:
- Done when:

Keep implementation-complete, approved, merged, deployed and verified as distinct states, even if the tracker combines them. Record the evidence before moving an item to the team's final state.
