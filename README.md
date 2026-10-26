# DesiDigitalPrints

A React + Vite web app for browsing print templates and customizing a chosen design. The landing page lists templates, a generator wizard walks through customizing the selected template, and an admin area manages the site.

## What it does

- Landing page (`/`): shows templates from the `templates` collection in PocketBase, via `src/lib/pb`. If that fetch fails, the app logs a warning and falls back to an empty list.
- Design (`/design`): the Generator Wizard (`src/components/GeneratorWizard.jsx`) for the template chosen on the landing page. Visiting `/design` with no template selected redirects back to `/`.
- Admin (`/admin`): an admin login page. A valid PocketBase auth session sends the admin to `/admin/dashboard` instead.
- Admin dashboard (`/admin/dashboard`): the admin area, with logout that clears the PocketBase auth store. Visiting it while logged out redirects to `/admin`.
- Toasts: a toast container is shown at the top-right of every page.

## Tech stack

- React 19 and Vite 5 (see `package.json`)
- React Router (`react-router-dom`) for routing
- PocketBase for templates and admin auth (see `src/lib/pb` and `pocketbase.md`)
- Tailwind CSS and DaisyUI for styling
- GrapesJS for page building, Framer Motion for animation, Lucide React for icons
- Express, SQLite (`sqlite3`) and Multer are also listed in `package.json`

## How to run

```bash
npm install
npm run dev
```

Build for production and preview the build:

```bash
npm run build
npm run preview
```

Lint the project:

```bash
npm run lint
```

## Project structure

```
index.html              # Entry page
vite.config.js          # Vite configuration
tailwind.config.js      # Tailwind configuration
postcss.config.js       # PostCSS configuration
eslint.config.js        # ESLint configuration
pocketbase.md           # PocketBase notes
src/
  main.jsx              # App entry point
  App.jsx               # Routes: /, /design, /admin, /admin/dashboard
  App.css, index.css    # Styles
  assets/               # Static assets
  components/
    LandingPage.jsx     # Template listing
    GeneratorWizard.jsx # Design customization wizard
    admin/
      AdminLogin.jsx    # Admin login
      AdminDashboard.jsx # Admin dashboard
  lib/                  # PocketBase client (pb)
  utils/                # Utilities
server/                 # Server directory
hf-backend/            # Backend directory
public/                 # Public files
```
