# Stage 6: Session Management

This stage establishes secure, persistent user sessions using server-side cookies and the SQLite database.

## Stage 6 Task 1: Backend Session Setup
1.  **Dependencies:**
    -   Install `express-session` in `apps/api`.
    -   Install a session store compatible with SQLite (e.g., `connect-sqlite3` or a Prisma-based session store if preferred for type safety).
2.  **Configuration:**
    -   Configure the session middleware in `app.js` (or `main.ts`):
        -   **Secret:** Load from `SESSION_SECRET` env var (add to `.env`).
        -   **Store:** Point to the SQLite database (can use the same `data/sqlite.db` or a separate `sessions.db`).
        -   **Cookie:** Set `httpOnly: true`, `maxAge`, and `secure: false` (for dev/localhost) or verify `NODE_ENV` for production.
        -   **Resave/SaveUninitialized:** Configure appropriately (usually `false`).

## Stage 6 Task 2: API Integration
1.  **Session Endpoint:**
    -   Create `GET /api/session`.
    -   If a session doesn't exist, one is created automatically by the middleware.
    -   Return `{ sessionId: req.sessionID, ... }`.
2.  **Verification:**
    -   Use `curl` or Postman to hit the endpoint twice.
    -   Verify the `Set-Cookie` header is received on the first request.
    -   Verify the same `sessionId` is returned on the second request (sending the cookie back).

## Stage 6 Task 3: Frontend Integration
1.  **Fetch Logic:**
    -   Update the frontend API client (e.g., `axios` or `fetch`) to include credentials (`credentials: 'include'`). This is critical for sending/receiving cookies.
2.  **UI Update:**
    -   In the `Shell` or `Dashboard`, fetch the session info.
    -   Display "Session ID: <id>" (masked or small font) in the footer or debug section.
3.  **Verification:**
    -   Open the app in two different browsers (or Incognito).
    -   Verify that they display **different** Session IDs.
    -   Refresh the page; verify the Session ID **persists**.
