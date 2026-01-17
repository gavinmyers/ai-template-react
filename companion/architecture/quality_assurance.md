# Stage 2: Quality Assurance

This stage establishes the testing and linting infrastructure for the application, ensuring code quality and build integrity.

## Stage 2 Task 1: Backend Quality Assurance (apps/api)
1.  **Install Dependencies:** Install `jest`, `eslint`, and necessary plugins/presets (e.g., `supertest` for integration tests) in `apps/api`.
2.  **Configuration:**
    -   Initialize ESLint configuration.
    -   Configure Jest to look for tests in the `tests` folder.
3.  **Scripts:** Update `package.json`:
    -   `lint`: Command to run ESLint.
    -   `test`: Command to run Jest.
4.  **Build Integration:**
    -   Ensure that the build process executes the tests. For a non-compiled Node.js app, this means adding a `RUN npm test` (or similar) instruction in the `Dockerfile`. The build must fail if tests fail.

## Stage 2 Task 2: Frontend Quality Assurance (apps/web)
1.  **Install Dependencies:** Install `vitest`, `jsdom`, `@testing-library/react`, and ensure ESLint is properly configured (already present from template, verify configuration).
2.  **Configuration:**
    -   Configure Vitest (in `vite.config.ts` or `vitest.config.ts`) to use `jsdom` environment and look for tests in the `tests` folder.
3.  **Scripts:** Update `package.json`:
    -   `test`: Command to run Vitest.
    -   `build`: Update the build script to run tests before building (e.g., `npm run test && tsc && vite build`).
4.  **Build Integration:**
    -   Update `Dockerfile` to run tests during the build process (e.g., `RUN npm run test` or ensure the `build` script is called).

## Stage 2 Task 3: Verification Cycle (Failing Test)
1.  **Backend:** Create a test file `apps/api/tests/fail.test.js` with a test case that is guaranteed to fail.
2.  **Frontend:** Create a test file `apps/web/tests/fail.test.tsx` with a test case that is guaranteed to fail.
3.  **Verify Failure:** Run the build process (or test commands) and confirm that they fail.

## Stage 2 Task 4: Verification Cycle (Passing Test)
1.  **Fix:** Update the failing tests in both `apps/api` and `apps/web` to pass.
2.  **Verify Success:** Run the build process (or test commands) and confirm that they succeed.
3.  **Lint Verification:** Run the lint commands for both apps and ensure they execute correctly (even if no errors are reported).
