# DesiDigitalPrints

A React + Vite web app for browsing print templates and customizing a chosen design. The landing page lists templates, a generator wizard walks through customizing the selected template, and an admin area manages the site.

## What it does

- Landing page (`/`): a portfolio gallery for Desi Digital Prints. Designs come from three sources: the PocketBase `images` collection, the PocketBase `templates` collection, and a built-in gallery of 30 curated designs (`CLOUD_DESIGNS` in `src/components/LandingPage.jsx`) that always works — each built-in design has a real title, occasion category and search keywords, so search (try "birthday" or "housewarming") and the category filters work even if the backend is unreachable. If the PocketBase occasions list is empty, built-in occasion categories are used instead. Orders are placed over WhatsApp via the buttons on each design.
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
  index.css             # Styles
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

## Deployment

The site is deployed on Netlify (https://desidigitalprints.netlify.app) and
auto-deploys from the `main` branch of this repository — pushing to `main`
publishes the site. Gallery photos are served from Cloudinary and the hero
video from Hugging Face; PocketBase (see `pocketbase.md`) is hosted as a
Hugging Face Space (`hf-backend/`).
