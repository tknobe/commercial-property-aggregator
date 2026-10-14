# SaaS Project Template

A minimal, opinionated starting point for building small SaaS applications.

The template provides a stable development foundation without assuming which database, cloud provider, AI provider, authentication system, or external services a project will need.

## Included

* FastAPI backend
* React + TypeScript frontend
* Python worker structure
* Docker Compose
* GitHub Actions
* Environment configuration
* Testing structure
* Claude Code project instructions

## Philosophy

Start small.

The template contains the common foundations that are useful across projects. Project-specific infrastructure should be added only when the project actually needs it.

For example, a project may later add:

* PostgreSQL
* Redis
* object storage
* authentication
* AI providers
* scraping or ingestion services
* search infrastructure
* cloud deployment

None of these are included by default.

## Local development

Make sure Docker Desktop is running and Docker is available from your environment.

Start the development environment:

```bash
docker compose up -d --build
```

Check the running services:

```bash
docker compose ps
```

The backend is available at:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/health
```

FastAPI documentation:

```text
http://localhost:8000/docs
```

Stop the environment:

```bash
docker compose down
```

## Project structure

```text
.
├── backend/
├── frontend/
├── worker/
├── tests/
├── scripts/
├── .github/
├── .env.example
├── CLAUDE.md
├── docker-compose.yml
├── Makefile
└── README.md
```

## Creating a project from this template

Create a new repository from this template or clone it and rename the project.

Then adapt the template to the actual application.

Typical additions may include:

```text
database
authentication
file uploads
AI integration
external APIs
scraping/import jobs
search
cloud infrastructure
```

Add these only when they solve a real requirement.

## Claude Code

`CLAUDE.md` contains the project rules and architecture guidelines for Claude Code.

Claude Code should inspect the existing project before making architectural changes and should prefer small, incremental changes over unnecessary rewrites.

## Development principle

The template is a starting point, not a finished SaaS platform.

Keep the foundation stable and let the actual project determine what gets added next.

