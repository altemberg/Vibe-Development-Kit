# AGENTS.md

All agents must follow `CLAUDE.md`.

## Agent Design Principle

Agents are role-based, not domain-based.

Good:
- Product Manager
- Software Architect
- Frontend Engineer
- Backend Engineer
- QA Engineer
- Code Reviewer

Bad:
- CRM Agent
- Meta Ads Agent
- WhatsApp Agent
- Dashboard Agent

Business context belongs to the card/spec.
Responsibilities belong to the agent.

## Available Agents

- `product-manager.md`
- `card-analyst.md`
- `card-spec-writer.md`
- `software-architect.md`
- `frontend-engineer.md`
- `backend-engineer.md`
- `qa-engineer.md`
- `code-reviewer.md`
- `documenter.md`

## Handoff Rule

Each agent must produce:

- one output artifact
- one minimal handoff for the next agent

Do not pass unnecessary context forward.
