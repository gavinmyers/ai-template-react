# STEP_3: Backend Foundation (The API Blueprint)

## Goal
Establish the mandated API surface area. Every application MUST implement these core endpoints to satisfy health checks, session management, and observability.

## Standard Endpoints

### 1. System Health & Metadata
- **`GET /api/health`**:
    - **Requirement**: Returns `200 OK`.
    - **Response Body**: `{ "status": "ok", "timestamp": "ISO8601_STRING", "version": "VERSION_STRING" }`
- **`GET /api/info`**:
    - **Requirement**: Fetches metadata from the `ApplicationInfo` table.
    - **Response Body**: `{ "name": "APP_NAME", "description": "APP_DESC" }`

### 2. Session Management
- **`GET /api/session`**:
    - **Requirement**: Initialize a `sid` cookie if missing. Upsert a record in the `SessionCounter` table.
    - **Response Body**: `{ "hasSession": true, "sessionId": "UUID", "visits": number }`
- **`POST /api/session/reset`**:
    - **Requirement**: Delete session record and clear cookie.
    - **Response**: `204 No Content`.

## Core Implementation Requirements
- **Framework**: Fastify.
- **Middleware**: `@fastify/cors` (enabled for all origins in dev) and `@fastify/cookie` (required for sessions).
- **Validation**: Every environment variable used must be checked via a `requireEnv()` helper that calls `process.exit(1)` on failure.
- **Logging**: Use `pino` (Fastify default) with custom request logging middleware to output `[ACCESS]` lines to the console.
- **Shutdown**: Listen for `SIGINT` and `SIGTERM` to close Prisma and the Fastify server cleanly.
