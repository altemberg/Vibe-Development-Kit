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

Each agent must create:

- `output.md`
- `handoff.yml`

The next agent should only read the handoff and explicitly referenced files.
