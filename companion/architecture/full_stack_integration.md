# Stage 5: Full Stack Integration

This stage connects the Frontend (MUI) to the Backend (SQLite API) to verify end-to-end functionality.

## Stage 5 Task 1: Frontend Data Fetching
1.  **API Client:**
    -   In `apps/web`, create a utility or hook (e.g., `useSystemInfo`) to fetch data from `/api/info`.
    -   Ensure CORS or Proxy configuration in Vite allows the request to reach `http://localhost:3000` (or the API container).

## Stage 5 Task 2: UI Display
1.  **Update Shell/Dashboard:**
    -   Import the fetch logic into the `Dashboard` or `Shell` component.
    -   Use Material UI `Typography` to display:
        -   "Application: <appName>"
        -   "Version: <version>"
    -   Handle loading and error states gracefully (e.g., using MUI `Skeleton` or `Alert`).

## Stage 5 Task 3: Final Verification
1.  **Integration Test:**
    -   Start the full stack: `docker-compose up`.
    -   Access `http://localhost:8080`.
    -   Verify that the page loads and displays "Application: AI Template" and "Version: 1.0.0" (from the seeded DB).
2.  **Automated Test (Optional but Recommended):**
    -   Write a frontend test that mocks the API response and asserts that the `Dashboard` component renders the version string correctly.
