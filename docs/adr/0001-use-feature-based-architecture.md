# ADR 0001 — Use Feature-Based Architecture

## Status

Accepted

## Context

AI-generated projects often become hard to maintain when code is organized only by technical type, such as large global folders for components, hooks, services, and utilities.

## Decision

VDK uses feature-based architecture as the default organization pattern.

## Consequences

- Feature context stays localized.
- Agents can work with less context.
- Code review becomes easier.
- Shared abstractions must be intentionally extracted.
