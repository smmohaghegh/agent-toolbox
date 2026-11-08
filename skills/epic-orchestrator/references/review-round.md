# Review rounds

Match reviewer roles to risk. Existing shared behaviour may need engineering review; security-sensitive changes need security input; regulated or specialist content needs the relevant domain approval. Do not assume documentation or isolated new pages are automatically low risk.

## Run the round

1. Collect submitted reviews, inline threads, conversation comments, CI results and QA findings across every PR in the round.
2. Verify each substantive claim against the current code and tested head. Treat reviewer claims and agent replies as leads until checked.
3. Present a decision table: reviewer, linked point, evidence, recommendation (fix/defer/disagree), rationale and blocking status.
4. Ask the owner for unresolved decisions. Create authorised follow-up tasks for deferrals with evidence and acceptance criteria; retain a pending record if tracker writes are unavailable.
5. Prepare a fix brief preserving comment identifiers. Obtain the required dispatch authority. Have the agent repeat the full VM implementation, test and repair loop until the accepted review points and regression criteria are demonstrated.
6. Have the agent explain each change and commit in draft replies. Post replies only when communication authorisation covers them. Leave thread resolution to the reviewer or agreed human process.
7. Prepare a concise re-review message for the owner, listing changes and validation.
8. Re-check required approvals and CI on the final PR head. A later push invalidates earlier readiness evidence where relevant.

## Owner questions

Collect unanswered PR questions into a numbered table with a recommendation and trade-off. Record the owner's decisions in the brief and PR description. Remove answered questions only after the decision is applied or explicitly deferred.

## Common traps

| Trap | Check |
|---|---|
| PR merged during the round | Check state immediately before every push |
| Unrelated commit appears in a history view | Verify the actual PR diff and commit association before reporting it |
| CI passed before a later push | Match checks to the final head SHA |
| One feedback channel was missed | Include review summaries, inline threads, conversation and QA |
| Defer silently becomes forget | Record a linked follow-up task and acceptance criteria |
