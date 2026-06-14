# VDK Constitution

## Principle 1 — Frontend First

The user experience must be visually defined before backend implementation begins.

## Principle 2 — Mock Data First

Use realistic mock data to validate flows, states, and UI behavior before connecting real services.

## Principle 3 — Reuse Before Create

Before creating new code, verify whether an existing component, hook, service, or pattern can be reused or extended.

This principle operates under Principle 11 — Framework First: official framework and design system components are evaluated before any project-level reuse.

## Principle 4 — Rule of Three

If a pattern appears three times, create an abstraction.

## Principle 5 — English Only

All source code, file names, folder names, comments, logs, events, and documentation must be written in English.

## Principle 6 — Test Critical Flows

Testing should increase confidence in critical behavior, not chase arbitrary coverage numbers.

## Principle 7 — Human-Orchestrated AI

AI agents assist the workflow, but humans orchestrate decisions, sequencing, and final approval.

## Principle 8 — Minimal Handoffs

Agents must pass only the context required for the next agent to continue.

## Principle 9 — Simplicity Over Cleverness

Prefer clear, maintainable solutions over clever abstractions.

## Principle 10 — Documentation Before Implementation

For medium and large cards, document the intent before implementation.

## Principle 11 — Framework First

Official framework and design system components must always be preferred over custom implementations.

Decision hierarchy:

1. Official Framework Component
2. Official Design System Component
3. Existing Project Component
4. Extension of Existing Component
5. New Custom Component

Creating a new component should always be the last option.

The goal is to maximize consistency, maintainability, accessibility, and development speed.
