# Stage 4: Database Implementation (SQLite)

This stage implements a persistent SQLite database using Prisma ORM, ensuring data survives container restarts while being excluded from version control.

## Stage 4 Task 1: Infrastructure & Configuration
1.  **Filesystem Setup:**
    -   Create a `data/` folder in the project root.
    -   Update `.gitignore` to include `data/` and `*.db` patterns to ensure the database is never committed.
2.  **Docker Configuration:**
    -   Update `docker-compose.yml` for the `api` service:
        -   Add volume mount: `./data:/app/data`.
        -   Set environment variable: `DATABASE_URL=file:/app/data/sqlite.db`.
3.  **Environment:**
    -   Update `.env` (and template) to include `DATABASE_URL`.

## Stage 4 Task 2: Prisma ORM Setup
1.  **Installation:**
    -   In `apps/api`, install dependencies:
        -   `npm install prisma --save-dev`
        -   `npm install @prisma/client`
2.  **Initialization:**
    -   Run `npx prisma init` (or manually create `prisma/schema.prisma`).
3.  **Schema Definition:**
    -   Define a `SystemInfo` model in `schema.prisma`:
        ```prisma
        model SystemInfo {
          id        Int      @id @default(autoincrement())
          appName   String
          version   String
          createdAt DateTime @default(now())
        }
        ```
    -   Ensure the `datasource` provider is "sqlite" and url is env("DATABASE_URL").
    -   Ensure the `generator` includes `binaryTargets = ["native", "linux-musl-openssl-3.0.x"]` (or appropriate linux target for the Docker Node image) to ensure the client works inside Docker.

## Stage 4 Task 3: Data Access & API
1.  **Client Singleton:**
    -   Create `apps/api/src/db/client.ts` to export a singleton instance of `PrismaClient`.
2.  **Seeding:**
    -   Create a seed script (e.g., `prisma/seed.ts`) that upserts a default record:
        -   `appName`: "AI Template"
        -   `version`: "1.0.0"
    -   Add `prisma.seed` to `package.json`.
3.  **API Endpoint:**
    -   Create an endpoint `GET /api/info`.
    -   Use the Prisma client to fetch the `SystemInfo`.

## Stage 4 Task 4: Backend Verification
1.  **Test Database:**
    -   Create a test file `apps/api/tests/db.test.js` (or `.ts`).
2.  **Test Logic:**
    -   Connect to the DB.
    -   Write a new `SystemInfo` record.
    -   Read it back.
    -   Verify the data matches.
    -   Clean up (delete the record).
3.  **Execution:**
    -   Run the test inside the container or via `docker-compose exec api npm test` to prove persistence works.
