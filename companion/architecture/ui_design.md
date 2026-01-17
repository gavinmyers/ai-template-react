# Stage 3: UI Design System

This stage focuses on establishing a robust UI foundation in `apps/web` using Material UI (MUI), ensuring a consistent look and feel and preparing the application for feature development.

## Stage 3 Task 1: Installation & Configuration
1.  **Install Dependencies:**
    -   In `apps/web`, install the core MUI libraries: `@mui/material`, `@emotion/react`, `@emotion/styled`.
    -   Install icons: `@mui/icons-material`.
    -   Install font: `@fontsource/roboto`.
2.  **Clean Up:**
    -   Remove default Vite/React CSS files (`App.css`, `index.css`) if they conflict with MUI's baseline.
    -   Remove references to these files in `App.tsx` and `main.tsx`.

## Stage 3 Task 2: Theming & Global Styles
1.  **Theme Configuration:**
    -   Create `apps/web/src/theme/theme.ts`.
    -   Define and export a custom theme using `createTheme` (start with a primary/secondary color palette).
2.  **App Integration:**
    -   In `apps/web/src/main.tsx` (or `App.tsx`):
        -   Import `ThemeProvider` from `@mui/material/styles`.
        -   Import `CssBaseline` from `@mui/material`.
        -   Import the `theme` from `./theme/theme`.
        -   Import Roboto font (e.g., `import '@fontsource/roboto/300.css';` etc.).
    -   Wrap the root application component with `<ThemeProvider theme={theme}>` and include `<CssBaseline />` as a child.

## Stage 3 Task 3: Application Shell (Layout)
1.  **Component Creation:**
    -   Create `apps/web/src/components/layout/Shell.tsx`.
2.  **Implementation:**
    -   Implement a responsive layout using MUI components (`Box`, `AppBar`, `Toolbar`, `Drawer`, `Container`).
    -   Include a Header (AppBar) with a title.
    -   Include a Sidebar (Drawer) for navigation (can be temporary or permanent based on screen size).
    -   Include a generic "Main Content" area using `component="main"`.
3.  **Route Integration:**
    -   Update `App.tsx` to use the `Shell` component as the wrapper for the page content.

## Stage 3 Task 4: Component Showcase (Verification)
1.  **Dashboard Page:**
    -   Create `apps/web/src/pages/Dashboard.tsx`.
2.  **Content:**
    -   Use a `Grid` layout.
    -   Add sample components to verify theming:
        -   **Cards:** A card with a title and content.
        -   **Buttons:** Examples of `variant="contained"`, `variant="outlined"`, and `color="secondary"`.
        -   **Inputs:** A `TextField` and a `Switch`.
3.  **Render:**
    -   Render this `Dashboard` inside the `Shell` in `App.tsx`.
4.  **Verification:**
    -   Ensure the application runs (`npm run dev`) and displays the shell and dashboard with the correct theme colors and font.

## Stage 3 Task 5: Testing Support
1.  **Test Utility:**
    -   Create `apps/web/src/tests/test-utils.tsx`.
    -   Implement a custom render function that wraps the component under test with the `ThemeProvider` and the project theme.
    -   Re-export everything from `@testing-library/react`.
2.  **Update Tests:**
    -   Update `apps/web/tests/fail.test.tsx` (and any other existing component tests) to use this custom render function if they test components relying on the theme.
