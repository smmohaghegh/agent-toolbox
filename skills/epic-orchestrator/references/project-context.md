# Project context

Create or update a small project record in the agreed working location. Use established project records where available; this template has no mandatory external integration.

## Context template

| Field | Record |
|---|---|
| Outcome and epic owner | Intended user outcome; accountable decision-maker |
| Source repositories | Repository URLs or local paths; default branches; repository instructions |
| Work tracker | Tool or local file; initiative/epic/task mapping; required fields and status meanings |
| Review roles | Engineering, QA, security, accessibility or domain specialists as applicable |
| Build environment | Dedicated development VM; host/provider, connection, complete stack and authoritative operations runbook |
| Full development access | Shell, sudo/root where required, repository writes and pushes, package installation, services, development DB, browser and tests; verify actual capability |
| Mission loop | Acceptance criteria, representative test data, evidence requirements, progress location and escalation boundaries |
| Build agent | Product and supported launch, brief-delivery and status interfaces |
| Durable working files | Location of RUN.md, PROGRESS.md, BLOCKED.md, DECISIONS.md and SUMMARY.md, or equivalents |
| Authorisation | Who can instruct agents, change infrastructure, update tickets, merge, deploy and contact people; any standing scope |
| Release mechanics | Workflow or command; trigger; selected ref/artifact; environments; migration timing; release runbook |
| Dependencies | Other repositories, content, schema, configuration, feature flags and consumers |
| Verification | Approved smoke tests, monitoring and read-only production checks |
| Recovery | Rollback or roll-forward procedure; backups; accountable operator |
| Reporting | Time zone, update format and expected cadence |

Leave unknowns explicit. Ask only for information that blocks the current stage. Never copy credentials into this record.

## Tool adaptation

Use the connected tracker and version-control tools where suitable. Jira, Linear, GitHub Issues and a local task file are possible tracker choices, not requirements. Use PR or merge-request terminology to match the host.

Use repository CI and infrastructure definitions to verify release behaviour. A runbook is a starting point; resolve discrepancies before deployment. Do not presume a branch is called main, a green run deployed anything, or a production workflow uses its dispatch branch.

Read the host's current supported installation instructions if setup is requested. For a file-based host, the distributable unit is the complete epic-orchestrator folder, including SKILL.md, agents and references. Do not claim an extracted archive is installed until the host recognises it.
