# STEP_1: Repository & Monorepo Structure

## Goal
Establish the foundational directory structure and configuration for a Turborepo-managed monorepo.

## Tasks

### TASK_0: Git Initialization
- Initialize a new git repository in the root directory.
- Create a `.gitignore` that excludes `node_modules`, `dist`, `build`, logs, and environment secrets.

### TASK_1: Turborepo Scaffolding
- Initialize a `pnpm` workspace (`pnpm-workspace.yaml`).
- create `turbo.json` to define build pipelines (e.g., `build`, `test`, `lint`, `dev`).
- Create the following directory structure:
    ```text
    /
    ├── apps/
    │   ├── api/       # Backend service
    │   └── web/       # Frontend service
    ├── packages/
    │   └── database/  # Shared Prisma client & schema
    ├── e2e/           # Shared E2E tests (Playwright)
    ├── .gitignore
    ├── package.json   # Root scripts
    ├── pnpm-workspace.yaml
    └── turbo.json
    ```

### TASK_2: Root Configuration
- Define root-level scripts in `package.json` to orchestrate common tasks:
    - `dev`: Run all apps in development mode.
    - `build`: Build all apps and packages.
    - `test`: Run all tests (unit + e2e).
    - `lint`: Lint all code.
    - `db:migrate`: Run database migrations.
- Install global dev dependencies (e.g., `typescript`, `eslint`, `prettier`).