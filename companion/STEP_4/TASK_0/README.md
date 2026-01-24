# STEP_4: Database & Persistence (The Data Blueprint)

## Goal
Establish the mandated database schema. Every application MUST start with these models to support the Standard API Baseline.

## Required Models (Prisma)

### 1. `ApplicationInfo`
Used by `GET /api/info` to identify the instance.
- `id`: Int (Autoincrement, ID)
- `name`: String
- `description`: String?
- `updatedAt`: DateTime (Updated automatically)

### 2. `SessionCounter`
Used by `GET /api/session` to track basic analytics.
- `id`: Int (Autoincrement, ID)
- `sessionId`: String (Unique Index)
- `visits`: Int (Default: 0)
- `updatedAt`: DateTime

## Standard Workflow
1.  **Sync**: The API must ensure at least one `ApplicationInfo` record exists on startup.
2.  **Migrations**: Use `prisma migrate deploy` for all non-local environments.
3.  **Reset**: The `pnpm run test` script MUST perform a full schema drop and migrate for every run.