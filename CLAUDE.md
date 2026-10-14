# Project Instructions

## Purpose

This repository is a reusable SaaS project template.

The template provides a small, stable foundation for new projects. Build project-specific functionality on top of this foundation rather than adding infrastructure in advance.

## Stack

* Backend: Python + FastAPI
* Frontend: React + TypeScript
* Background jobs: Python worker
* Local development: Docker Compose
* Version control: Git
* CI: GitHub Actions

## Core principles

Keep the architecture simple.

Do not add a database, queue, cache, cloud service, authentication system, search engine, or third-party platform unless the current project has a concrete requirement for it.

Prefer the simplest solution that solves the current problem.

Do not introduce a new framework or service just because it is common in SaaS applications.

## Project structure

Keep responsibilities separated:

* `backend/` contains the API and backend business logic.
* `frontend/` contains the user interface.
* `worker/` contains slow or background operations.
* `tests/` contains project-level tests.
* `.github/` contains CI configuration.
* `scripts/` contains development and maintenance scripts.

Keep HTTP concerns in API routes.

Keep non-trivial business logic in services rather than route handlers.

Keep background work out of HTTP request handlers when the work is slow, expensive, or retryable.

## Docker

Use Docker Compose for local development.

Do not require developers to install project-specific runtime dependencies directly on the host unless there is a clear reason.

Keep container configuration simple and readable.

Do not add infrastructure to `docker-compose.yml` until the project needs it.

## Database

This template does not include a database by default.

When a project requires persistence, choose and add the simplest appropriate database.

PostgreSQL is the default database choice unless there is a concrete reason to use something else.

When a database is introduced:

* Keep credentials in environment variables.
* Use migrations for schema changes.
* Never commit secrets.
* Never put credentials directly in source code.
* Keep database-specific code isolated from unrelated application logic.

## AI

When using an LLM:

* Prefer structured outputs when possible.
* Keep provider-specific code isolated.
* Keep prompts easy to inspect and version.
* Never hardcode API keys.
* Never log secrets.
* Put slow or expensive AI operations in background jobs when appropriate.
* Make failures and retries explicit.

Do not add an AI provider to the template unless a specific project requires it.

## External data and scraping

When a project collects external data:

* Respect terms of service and applicable access rules.
* Respect rate limits.
* Use careful retry logic.
* Store source URLs and timestamps where useful.
* Normalize external data before persistence.
* Make ingestion idempotent where possible.

Never bypass authentication, CAPTCHAs, paywalls, or technical access controls.

## Testing

Add tests for important business logic and data transformations.

Run relevant tests before committing.

Prefer small, focused tests over large end-to-end tests when unit tests are sufficient.

## Configuration and secrets

Use environment variables for configuration that differs between environments.

Do not commit:

* `.env` files containing secrets
* API keys
* passwords
* credentials
* tokens
* private certificates

Keep `.env.example` up to date when new environment variables are introduced.

## Git

Use small, descriptive commits.

Examples:

* `feat: add procurement importer`
* `fix: handle duplicate listings`
* `test: add odds normalization tests`
* `docs: update setup instructions`

Do not commit generated files, secrets, local databases, or unnecessary build artifacts.

## Dependencies

Before adding a dependency, ask:

1. Do we actually need it?
2. Does the project already solve this problem another way?
3. Does the dependency add significant complexity?
4. Is there a simpler alternative?

Do not add services or libraries speculatively.

## Working with Claude Code

Before making architectural changes:

1. Inspect the existing structure.
2. Understand the current implementation.
3. Reuse existing patterns.
4. Make the smallest reasonable change.
5. Run relevant tests and checks.
6. Update documentation when behavior or setup changes.

Do not rewrite working parts of the project without a concrete reason.

Do not create duplicate abstractions when an existing one is sufficient.

## Definition of done

Before considering a task complete:

1. The implementation works.
2. Relevant tests pass.
3. Docker Compose still starts when applicable.
4. No secrets were added.
5. Documentation is updated when necessary.
6. The implementation follows the existing project structure.
7. Unnecessary dependencies or services were not introduced.

