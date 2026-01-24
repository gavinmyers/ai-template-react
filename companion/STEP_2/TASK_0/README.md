# STEP_2: Frontend Foundation (The UI Blueprint)

## Goal
Establish the mandated UI architecture. Every application MUST start with this layout and state management strategy.

## Required Components

### 1. The Layout Shell (`Layout.tsx`)
- **Requirement**: A persistent 2-column layout.
- **Sidebar**: Fixed width (e.g., `w-64`), contains the Logo and Navigation links.
- **Main**: Auto-scrolling area using `<Outlet />` for child routes.

### 2. Standard Views
- **Dashboard (`Dashboard.tsx`)**:
    - **Endpoint**: Fetches from `/api/health`.
    - **Display**: Shows "System Status" cards (Uptime, Timestamp, Version).
- **Settings (`Settings.tsx`)**:
    - **Endpoint**: Fetches from `/api/info`.
    - **Display**: Allows editing application metadata.

## Required Stack & Patterns
- **Framework**: Vite + React + TypeScript.
- **Navigation**: `react-router-dom` (BrowserRouter).
- **Data Fetching**: `@tanstack/react-query` (QueryClientProvider).
- **API Client**: `axios` with base URL configuration.
- **Styling**: **Tailwind CSS** for layout/utility and **Material UI (MUI)** for complex components (Tables, Modals).
- **Icons**: `lucide-react`.
