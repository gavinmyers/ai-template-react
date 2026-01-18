# STEP_1/TASK_1: pnpm Workspace Validity

## Goal
Prove this repo is a real pnpm workspace and that pnpm can see packages.

## Run Commands
```powershell
# 1) Workspace file exists and is parseable
Test-Path .\pnpm-workspace.yaml
Get-Content .\pnpm-workspace.yaml

# 2) pnpm sees the workspace root and lists packages
pnpm -w -v
pnpm -w list -r --depth -1

# 3) Verify the expected top-level layout exists
Test-Path .\apps
Test-Path .\packages
ls .\apps
ls .\packages
```

## Verification Criteria
- `pnpm -w list -r --depth -1` prints at least:
    - the root workspace package, and
    - one or more packages under `apps/` and/or `packages/`
- `apps/` and `packages/` exist and list contents.

## Record
Add to `.companion/APPLICATION.md`:
- Workspace root name
- Package count (rough is fine, e.g. "apps=1, packages=1")
