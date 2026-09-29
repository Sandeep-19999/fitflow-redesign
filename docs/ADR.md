# Architecture Decision Record 01 FitFlow Technology Stack

**Status:** Proposed for IT3060 HCI Lab Exercise 05.

## Context

FitFlow needs a timely Android and iOS redesign, useful browser access, adaptive workouts, easier meal logging and private social features. It must protect personal fitness data and allow an AI recommendation to be reviewed by the user.

## Decision

Use React Native for mobile and React Native Web for suitable browser screens. Use Node.js and Express for the main API, PostgreSQL for structured fitness records, Firebase Authentication and Cloud Firestore for identity and live community content, a separate Python AI service with optional LiteRT inference on device, and Redis for short-lived non-sensitive caching.

## Rationale

The choice follows the case study's React Native, Node.js and Firebase direction. It supports mobile code sharing and faster delivery while separating model processing and private fitness records from community content. The weighted comparison is documented in `decision-matrix.md`.

## Consequences

Two data stores and an AI service add integration and operational work. Define clear data ownership and user-ID mapping. Verify API tokens, enforce circle membership rules, monitor costs, and test browser and native modules. Validate accessibility, privacy, performance and model quality in a prototype before deployment.

## Critical flows

1. Workout: app → API → PostgreSQL records → AI service → editable recommendation → API → PostgreSQL.
2. Social: app → Firebase Authentication → membership-scoped Firestore posts → live circle updates.
3. Nutrition: meal photo → local or opt-in cloud inference → user confirms foods and portions → API → PostgreSQL.
