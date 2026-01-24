# Project Roadmap

This companion guide outlines the step-by-step process for building a production-ready, containerized full-stack application using a monorepo structure. It is designed to be a reusable template for future projects.

## Project Architecture
- **Monorepo**: Managed by Turborepo (`apps/api`, `apps/web`, `packages/database`).
- **Frontend**: Vite + React + Tailwind CSS + Material UI.
- **Backend**: Fastify (Node.js) + FFmpeg + Prisma ORM.
- **Database**: PostgreSQL.
- **Infrastructure**: Docker Compose with multi-environment support (`local`, `dev`, `test`, `prod`).
- **Testing**: Vitest (Unit) + Playwright (E2E).

## Reference Examples
Detailed configuration files (e.g., `package.json`, `docker-compose.yml`, `.env`) are available in the **[examples](./examples/)** directory. Use these as a starting point ("Golden Master") for new projects.

## Workflow Overview

### [STEP_0: Environment Setup](./STEP_0/TASK_0/README.md)
- **TASK_0**: Verify local development environment and prerequisites.

### [STEP_1: Repository & Monorepo Structure](./STEP_1/TASK_0/README.md)
- **TASK_0**: Initialize Git repository.
- **TASK_1**: Scaffold Turborepo structure.
- **TASK_2**: Configure shared packages (`@repo/database`, `@repo/config`).

### [STEP_2: Frontend Foundation](./STEP_2/TASK_0/README.md)
- **TASK_0**: Initialize Vite + React workspace (`apps/web`).
- **TASK_1**: Configure Styling (Tailwind + MUI).
- **TASK_2**: Setup Unit Testing (Vitest).
- **TASK_3**: Setup E2E Testing (Playwright).

### [STEP_3: Backend Foundation](./STEP_3/TASK_0/README.md)
- **TASK_0**: Initialize Fastify workspace (`apps/api`).
- **TASK_1**: Configure FFmpeg and core services.
- **TASK_2**: Implement API logging and health checks.

### [STEP_4: Database & Persistence](./STEP_4/TASK_0/README.md)
- **TASK_0**: Setup PostgreSQL container.
- **TASK_1**: Initialize Prisma ORM.
- **TASK_2**: Define Schema and Migration Workflow.
- **TASK_3**: Integrate Database with API.

### [STEP_5: Containerization & Deployment](./STEP_5/TASK_0/README.md)
- **TASK_0**: Create Dockerfiles for all services.
- **TASK_1**: Define Nginx Proxy configuration.
- **TASK_2**: Implement Multi-Environment Docker Compose (`dev`, `test`, `prod`).
- **TASK_3**: Final Verification and Secrets Management.