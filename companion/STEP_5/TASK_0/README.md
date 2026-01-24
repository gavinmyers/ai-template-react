# STEP_5: Containerization (The Infrastructure Blueprint)

## Goal
Establish the mandated orchestration and routing strategy. Every application MUST use this multi-environment Docker setup.

## Standard Environments

### 1. `local` / `dev`
- **Goal**: Rapid development.
- **Port**: Host maps to individual service ports (e.g., 3001, 5173).
- **Volumes**: Map local source code into containers for hot-reloading.

### 2. `test` (Ephemeral)
- **Goal**: Full-stack CI/CD validation.
- **Cleanup**: Containers and volumes MUST be removed automatically (`--volumes` flag).
- **Networking**: Isolated bridge network for internal communication.

### 3. `prod` (Gateway)
- **Goal**: High availability.
- **Proxy**: All traffic MUST flow through **Nginx**.
- **Routing**:
    - `/` -> Serve static React files.
    - `/api/` -> Proxy to Fastify container.

## Required Configuration Files
- **`.env.prod.secrets`**: Mandatory file for DB passwords and session keys (Ignored by Git).
- **`nginx.conf.template`**: Used by the `nginx:alpine` image to dynamically inject the API hostname.
- **`docker-compose.yml`**: Uses `${VAR}` syntax for all ports and image names.
