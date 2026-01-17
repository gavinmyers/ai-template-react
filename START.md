# Agent Workflow Instructions

Follow these steps to manage the application lifecycle and track progress:

## Initialization
1.  **Read Lifecycle:** Start by reading `companion/README.md` to understand the application stages.
2.  **Analyze Architecture:** Read each architectural document referenced in the lifecycle (e.g., files in `companion/architecture/`).
3.  **Check Progress:** Inspect the `tasks/` folder to identify completed tasks.

## Strict Adherence & Failure Handling
**CRITICAL:**
-   **No Deviations:** You must follow instructions **exactly**. Do not change port numbers, file paths, or versions unless explicitly instructed.
-   **Stop on Error:** If a command fails, a resource (like a port) is unavailable, or a file is missing, **STOP IMMEDIATELY**.
-   **No Auto-Fixing:** Do not attempt to fix environment issues (e.g., killing processes, changing ports) or code issues without asking the user first.
-   **Report:** Report the specific error or discrepancy to the user and wait for input.

## Task Execution
-   A task is considered complete if a corresponding file exists in the `tasks/` folder named `STAGE_<NUMBER>_TASK_<NUMBER>.md`.
-   Identify the first incomplete task based on the architectural definitions and the contents of the `tasks/` folder.
-   Execute the task according to the specifications in the architectural documents.

## Completion & Documentation
When a task is successfully finished, create a status file in the `tasks/` directory:
-   **Filename:** `STAGE_<NUMBER>_TASK_<NUMBER>.md`
-   **Content:**
    -   A description of the work performed.
    -   A clear statement that the task is completed.

## Continuity
Always refer to `tasks/` at the beginning of a session to determine the current state and next steps.