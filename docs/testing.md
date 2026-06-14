# Testing Guide

VDK prioritizes meaningful tests over arbitrary coverage percentages.

## What to Test

- User flows
- Forms
- Business rules
- Permissions
- Data transformations
- Webhooks
- Critical integrations

## What Not to Test

- Implementation details
- Pure styling
- Library internals
- Trivial wrappers

## Recommended Tools

- Vitest for unit tests
- React Testing Library for component behavior
- Playwright for E2E flows
