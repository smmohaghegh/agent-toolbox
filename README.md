# Agent Toolbox

My collection of reusable skills, tools and workflows for building software with AI agents.

The aim is practical: give agents the environment and feedback they need to carry a goal through to a verified result, with clear human decision points.

## Toolbox

| Tool | What it does | Get started |
|---|---|---|
| Epic Orchestrator | Coordinates an epic from idea through implementation, review, release and clean-up | [Skill](skills/epic-orchestrator/SKILL.md) · [Download package](packages/epic-orchestrator.zip) |

## The central idea

Agents work inside a dedicated development VM with full access to the development environment: repositories, shell, services, development databases, browsers, test tools and package installation, including administrative access where needed and authorised.

That lets them close the loop themselves:

1. Implement the next change.
2. Run the complete development stack and exercise the actual user journey.
3. Inspect failures and repair the code or environment.
4. Repeat until evidence demonstrates the agreed acceptance criteria.

An approved mission covers routine development iterations. Humans remain responsible for scope decisions, review, merging and release authority. Development VM access does not imply production access.

## Use Epic Orchestrator

Download [the package](packages/epic-orchestrator.zip) and import it into an assistant that supports skills, using that host's installation process. The archive includes a getting-started guide.

For a host that loads skills from folders, use the complete [skills/epic-orchestrator](skills/epic-orchestrator) directory. Keep its main instructions, agent metadata and references together.

Start with:

```text
Use epic-orchestrator to plan this epic: [outcome].
Prepare the first mission brief for an agent running in a dedicated
development VM with full access. Do not dispatch the brief yet.
```

Provide your repositories, work tracker, VM setup, coding agent and reporting time zone. The workflow adapts to your tools and release process.

## Repository layout

| Location | Contents |
|---|---|
| skills/ | Reusable agent skills and their supporting references |
| packages/ | Ready-to-share skill archives |

## Suggestions and improvements

Open an issue with the problem, a concrete example and the behaviour you would like to see. Keep contributions general enough to work outside one organisation. Leave credentials, customer data and internal infrastructure details out of examples.
