# AI Agents

VDK agents are role-based and domain-agnostic.

## Available Agents

- Product Manager
- Card Analyst
- Card Spec Writer
- Software Architect
- Frontend Engineer
- Backend Engineer
- QA Engineer
- Code Reviewer
- Documenter

## Agent Rule

Business context belongs to cards and specs.
Agent responsibilities belong to agent files.

## Handoff Rule

Each agent must create, namespaced by card id:

- an output artifact under `artifacts/output/<card-id>/`
- a handoff for the next agent under `artifacts/input/<card-id>/handoff.yml` (from `templates/handoff-template.yml`)

The next agent should read only `CLAUDE.md`, the card, the latest handoff, and the files it explicitly references.
