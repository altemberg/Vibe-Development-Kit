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

## ADRs

Important architecture decisions must be recorded in `docs/adr`.
