# Stage 1: Application Initialization (Monorepo)

This stage defines the steps to initialize a Monorepo application with a clear separation between Client (Frontend) and Server (Backend).

## Stage 1 Task 0: Application Metadata
1. Check if `application.json` exists at the root of the repository.
2. If it does not exist, create it with an empty JSON object `{}`.

## Stage 1 Task 1: Monorepo Root Setup
1. Prompt the user for a project name.
2. Create a folder at the repository root using that project name (e.g., `./my-project/`). **All subsequent steps happen inside this folder.**
3. Update `application.json` in the repo root with the application name.
4. Inside the project folder, create a `package.json` to define the workspace:
    -   `private`: `true`
    -   `workspaces`: `["apps/*", "packages/*"]`
5. Create the directory structure: `apps/api` and `apps/web`.

## Stage 1 Task 2: Docker Infrastructure
1. Create a root `docker-compose.yml` in the project folder.
2. Define two services:
    -   `api`: Builds from `./apps/api`. Maps port `3000`. Volumes: `./logs:/app/logs`, `./config:/app/config`.
    -   `web`: Builds from `./apps/web`. Maps port `8080`.
3. Create a root `.env` file containing:
    -   `APP_NAME=<project name>`
    -   `API_PORT=3000`
    -   `WEB_PORT=8080`
4. Create global `logs/` and `config/` folders in the project root (to be mounted by the API).
5. Create a `config/config.json` file with default content: `{ "environment": "development" }`.

## Stage 1 Task 3: Backend Implementation (apps/api)
1. Initialize a basic Node.js/Express application in `apps/api`.
2. Create `apps/api/Dockerfile` (Node environment).
3. Implement `init.js` or `index.js` in the API to:
    -   Write startup logs to `/app/logs/app.log`.
    -   Read configuration from `/app/config/config.json`.
4. Ensure `package.json` in `apps/api` includes the start scripts.

## Stage 1 Task 4: Frontend Implementation (apps/web)
1. Initialize a Vite/React/TypeScript application in `apps/web`.
2. Configure Vite (`vite.config.ts`) or the start command to listen on port `8080` and expose the host (e.g., `server: { port: 8080, host: true }`).
3. Create `apps/web/Dockerfile` (Node environment, typically nginx or serve for production, or vite dev server for development).
4. Ensure the frontend is configured to verify it runs successfully.

## Stage 1 Task 5: Verification
1. Run `docker-compose up --build`.
2. Verify `api` is running on port 3000 and logging to the root `logs/` folder.
3. Verify `web` is running on port 8080.