# Architecture Guide

## Recommended Architecture

VDK uses feature-based architecture.

```txt
src/
├── app/
├── components/
│   ├── ui/
│   └── shared/
├── features/
│   └── feature-name/
│       ├── components/
│       ├── hooks/
│       ├── mock-data/
│       ├── schemas/
│       ├── tests/
│       └── types.ts
├── lib/
└── server/
    ├── actions/
    ├── repositories/
    ├── services/
    ├── validators/
    └── integrations/
```

## Rules

- Shared UI goes in `components/shared`.
- Generic shadcn components go in `components/ui`.
- Feature-specific code stays inside `features/<feature-name>`.
- Backend logic stays inside `server`.
- Business logic must not live inside UI components.
- Mock data must not be mixed with real data access.

## UI Architecture

The primary design system for VDK projects is shadcn/ui.

Rules:

- shadcn/ui is the default source of UI components.
- Official shadcn blocks should be preferred when applicable.
- Shared components should wrap or extend shadcn components instead of replacing them.
- Custom components should only be created when no suitable shadcn solution exists.

The expected decision flow is:

```txt
shadcn/ui
↓
Project Shared Component
↓
Feature Component
↓
Custom Component
```

Avoid creating alternative implementations of existing shadcn patterns.

This reflects Principle 11 — Framework First from the Constitution.

## ADRs

Important architecture decisions must be recorded in `docs/adr`.
