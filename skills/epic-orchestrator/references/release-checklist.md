# Release checklist

Use the project's release runbook and current pipeline definitions. Treat the items below as questions to verify, not claims about how a particular system deploys.

## Prepare the release record

Create an authorised release task or a local checklist linked to the epic. List blocking steps in execution order with an accountable owner, evidence, environment and recovery action. Keep non-blocking communications and follow-ups explicit.

Record the exact source commit or immutable artifact digest, intended environments, release authority, migration plan and rollback or roll-forward path.

## Verify deployment mechanics

- Establish what each trigger actually does: build, publish, promote or deploy.
- Establish how each workflow chooses its ref or artifact. Resolve mutable tags to an immutable identifier and check for drift immediately before promotion.
- Identify who is using shared staging and coordinate before overwriting it.
- Determine migration timing, compatibility, locking and recovery. Check migration history against the actual schema before applying changes.
- Identify required secrets, settings, permissions and infrastructure; ensure they are present before the application reads them.
- Determine the supported cross-repository order, including mixed-version consumers and content publishers.
- Choose smoke tests and live checks tied to the acceptance criteria.
- Establish who can execute each step. Prepare everything reviewable before seeking a missing final approval.

## Execute within authority

1. Run required tests on the intended artifact and record results.
2. Deploy to a representative non-production environment using the documented mechanism.
3. Check the behaviour, integrations and relevant permissions there. Test production-like policy constraints where they matter.
4. Confirm approvals, final source/artifact identity and required release windows.
5. Follow the authorised merge and production deployment process. The orchestrator and build agent do not merge.
6. Observe the deployment run to a terminal result or report that monitoring is incomplete.
7. Verify live behaviour, artifact identity, migrations and dependent synchronisation.
8. Compare results to acceptance criteria and rollback triggers. Escalate failures; perform recovery only within authority.
9. Record the deployment time with a zone, run link, artifact and verification evidence.

Do not equate a release branch merge with production availability. A hotfix merged after a deploy needs its own verified release.

## Portable failure checks

| Risk | Verification |
|---|---|
| Cloud identity trust mismatch | Compare the provider's current subject/audience requirements with the actual workflow identity |
| First publish to new storage fails | Verify required initial objects, prefixes and permissions using the provider's documented behaviour |
| Production-only browser failure | Exercise relevant content-security policy and browser restrictions |
| Response contract mismatch | Check empty responses and status codes against actual client handling |
| Configuration read only at start-up | Apply configuration before the process starts and verify the effective value safely |
| Publisher precedes compatible consumer | Enforce compatibility-based release order and inspect import results |
| Migration ledger differs from schema | Reconcile through the documented recovery process before another migration |
| Staging artifact differs from production | Compare immutable identities, not workflow names or timestamps alone |

Mark irrelevant items as such with a reason. Add project-specific checks to the project runbook, not as universal rules here.
