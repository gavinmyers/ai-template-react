# STEP_0/TASK_0: Environment Verification

## Goal
Ensure the local development environment has all necessary tools installed and configured to support the project build.

## Prerequisites
Verify that the following tools are installed and accessible in your shell path.

### Core Tools
- **Git**: Version control.
- **Docker**: Container runtime.
- **Docker Compose**: Orchestration tool (ensure `docker compose` v2+).
- **Node.js**: JavaScript runtime (LTS version recommended).
- **pnpm**: Package manager (preferred over npm/yarn for monorepos).

### Optional but Recommended
- **FFmpeg**: For local backend testing without Docker (if applicable).
- **PostgreSQL Client (`psql`)**: For direct database interaction.

## Verification
Run the following commands to verify versions:
```bash
git --version
docker --version
docker compose version
node -v
pnpm -v
```

## Workspace Setup
1.  Create a `.gitignore` file.
2.  Ensure `.env` and `.env.*.secrets` files are ignored to prevent leaking sensitive data.
3.  Create a `.companion` directory for tracking local state (if using an agent).