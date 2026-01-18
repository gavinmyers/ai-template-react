# Main Roadmap

This directory contains the step-by-step guide for building the application.

## PowerShell Requirements

When executing shell commands in a PowerShell environment:
- **Avoid standard `curl`**: It is an alias for `Invoke-WebRequest` and may cause interactive prompts.
- **Use `curl.exe`**: For standard `curl` behavior.
- **Use `Invoke-RestMethod`**: For native PowerShell API interactions.
- **Use `-UseBasicParsing`**: When using `Invoke-WebRequest` to avoid Internet Explorer dependencies.

## General Guidelines

### Progress Logging
Each task will explicitly define its own recording requirements. When a task is completed, follow the specific logging instructions provided within that task's README.

### Workflow Continuity
To maintain absolute context and avoid configuration drift:
- **State Review**: Before starting any new task (STEP_X/TASK_Y), you must read all existing logs in the `.companion/` directory and the current `APPLICATION.md`.
- **Consistency Check**: Verify that the current state of the codebase matches the documented progress before proceeding with new modifications.

## Steps

- **[STEP_0: Environment Setup](./STEP_0/TASK_0/README.md)**: Initialize the project environment and verify capabilities.
