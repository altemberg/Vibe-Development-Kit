# CLAUDE.md

# Vibe Development Kit (VDK)

## Project Identity

This project follows the **Vibe Development Kit (VDK)** methodology.

The primary principle is:

> Build the complete frontend with realistic mock data first. Connect the backend, database, authentication, integrations, and automations only after the user experience has been validated.

Never start with the backend when the feature is not visually defined.

---

# Core Principles

1. Frontend First
2. Mock Data First
3. Reuse Before Create
4. Rule of Three
5. Test Critical Flows
6. Simplicity Over Complexity
7. Incremental Changes
8. Type Safety
9. Documentation Before Implementation
10. Human-Orchestrated AI Workflow

---

# Default Tech Stack

- Next.js App Router
- TypeScript
- Tailwind CSS
- shadcn/ui
- React Hook Form
- Zod
- Supabase or Prisma/PostgreSQL
- Vitest
- React Testing Library
- Playwright
- ESLint
- Prettier

---

# Required Development Workflow

Every feature must follow the appropriate pipeline based on complexity.

## Small Cards

Use a short pipeline:

```txt
PM → Frontend → Review
```

## Medium Cards

Use a standard pipeline:

```txt
PM → Architect → Frontend → Review
```

## Large Cards

Use the full pipeline:

```txt
PM → Analyst → Spec Writer → Architect → Frontend → Backend → QA → Review → Documenter
```

## Epic Cards

Split into multiple cards before implementation.

---

# Frontend-First Rule

When implementing a new feature:

Always:

- Create the UI first.
- Use realistic mock data.
- Validate user experience.
- Validate responsive behavior.
- Validate visual states.

Never:

- Create database tables first.
- Build APIs before the UI exists.
- Integrate external services before workflows are validated.
- Implement infrastructure before the feature is visually approved.

Required visual states:

- Loading
- Empty
- Error
- Success
- Populated data

---

# Mock Data Rules

Mock data must:

- Look realistic.
- Cover common scenarios.
- Cover edge cases.
- Include empty states.
- Include error scenarios when relevant.

Store mock data separately:

```txt
feature/
├── components/
├── hooks/
├── tests/
├── types/
└── mock-data/
```

Never hardcode mock data inside primary components.

---

# Naming Convention Rules

All source code must be written in English.

This includes:

- File names
- Folder names
- Functions
- Variables
- Components
- Types
- Database tables
- Database columns
- Events
- Logs
- Comments
- Documentation

## Naming Standards

| Item | Pattern | Example |
|---|---|---|
| Files | kebab-case | `lead-table.tsx` |
| Folders | kebab-case | `contact-management` |
| React Components | PascalCase | `LeadTable` |
| Functions | camelCase | `createLead()` |
| Variables | camelCase | `leadCount` |
| Types | PascalCase | `CampaignMetrics` |
| Database Tables | snake_case plural | `whatsapp_instances` |
| Database Columns | snake_case | `created_at` |
| Env Variables | UPPER_SNAKE_CASE | `DATABASE_URL` |
| Events | domain.action | `contact.created` |

---

# Component Reusability Rules

Before creating any new component, service, hook, utility, modal, table, form, card, or layout, always verify whether an existing implementation can be reused or extended.

## Reuse Before Create

Always ask:

1. Does a similar component already exist?
2. Can the existing component be extended?
3. Can the existing component receive props to support the new use case?
4. Can the existing component become more generic?

Only create a new component if reuse would make the code less maintainable.

## Preferred Hierarchy

1. Reuse existing component
2. Extend existing component
3. Create configurable component
4. Create new component

Creating a new component should be the last option.

## Rule of Three

If the same pattern appears three times, stop and create an abstraction.

- 1 occurrence = acceptable
- 2 occurrences = monitor
- 3 occurrences = refactor

Duplicated components, duplicated business logic, duplicated services, and duplicated UI patterns are technical debt.

Preferred solution:

```txt
Reusable > Configurable > Duplicated
```

---

# UI Standards

Use shadcn/ui as the primary design system.

Prioritize:

- Simplicity
- Readability
- Consistency
- Accessibility
- Responsive layouts

Prefer existing shadcn components over creating custom components.
Avoid unnecessary visual complexity.
Every screen should look like a production feature, not a prototype.

---

# Testing Standards

Prefer Test-Driven Development whenever practical.

Focus on testing:

- User behavior
- Business logic
- Permissions
- Validation
- Critical workflows

Avoid testing implementation details.
Avoid meaningless coverage.
Tests should increase confidence, not statistics.

Do not enforce arbitrary test coverage percentages.

---

# Backend Standards

Backend implementation begins only after frontend approval.

Recommended structure:

```txt
server/
├── repositories/
├── services/
├── actions/
├── validators/
└── integrations/
```

Rules:

- Validate all inputs.
- Validate all outputs.
- Use Zod schemas.
- Handle errors explicitly.
- Keep business logic out of UI components.
- Keep external integrations isolated.

---

# Database Standards

Before creating or modifying database structures:

1. Explain the change.
2. Identify affected entities.
3. Create explicit migrations.
4. Preserve existing data.
5. Consider multi-tenancy.
6. Consider auditability.

Never perform destructive changes without explicit approval.

---

# Security Rules

Never:

- Expose API keys.
- Commit secrets.
- Store secrets in frontend code.
- Bypass authentication.
- Bypass authorization.
- Create public endpoints without validation.

Always validate permissions on the server.
Never trust client-side validation.

---

# AI Safety Rules

Before modifying code:

1. Read relevant files.
2. Understand existing patterns.
3. Make the smallest possible change.
4. Preserve project conventions.
5. Avoid unnecessary rewrites.
6. Avoid architectural changes without justification.
7. Avoid introducing new dependencies without necessity.
8. Avoid modifying unrelated files.
9. Avoid mixing refactoring with feature implementation.
10. Explain important decisions.

When uncertain, ask for clarification instead of guessing.

---

# Card Lifecycle

Allowed status values:

```txt
backlog
analysis
specification
architecture
implementation
review
qa
documentation
done
blocked
```

Allowed complexity values:

```txt
small
medium
large
epic
```

Rules:

- Small cards may use a short pipeline.
- Medium cards may use a standard pipeline.
- Large cards must use the full pipeline.
- Epic cards must be split into smaller cards.

---

# Handoff Workflow

For complex features, use the VDK handoff pipeline.

Each agent must generate:

- a clear output artifact
- a minimal handoff file for the next agent

Agents must not pass unnecessary context forward.

The next agent should read:

1. `CLAUDE.md`
2. the current card
3. the previous handoff
4. only the files explicitly referenced in the handoff

Do not force the next agent to reread the entire codebase.

---

# Git Worktree Rules

Large features should use isolated Git Worktrees.

Example:

```bash
git worktree add .claude/worktrees/wt-card001-auth -b card001-auth
```

Rules:

- One card per worktree.
- One worktree per branch.
- Keep changes isolated.
- Merge only after validation.

Recommended naming:

```txt
wt-card001-auth
wt-card002-dashboard
wt-card003-billing
```

---

# Validation Commands

Before considering a task complete, run:

```bash
npm run lint
npm run typecheck
npm run test
```

For critical features:

```bash
npm run test:e2e
```

---

# Definition of Done

A task is complete only when:

- UI is finished.
- All visual states are implemented.
- Relevant tests exist.
- Lint passes.
- Type checking passes.
- Mock data is removed or properly isolated.
- Documentation is updated when required.
- Changes are summarized.

---

# Priority Order

When making decisions, prioritize:

1. User Experience
2. Product Functionality
3. Security
4. Maintainability
5. Performance
6. Scalability

Do not optimize prematurely.
Build clarity first.
