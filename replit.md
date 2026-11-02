# Crown Interiors — Commercial Construction Website

## Overview
Premium single-page website for Crown Interiors, an Auckland-based commercial and residential interior construction firm. Positioned as a corporate, tier-2 contractor with tender-ready presentation. Features 28 real projects from the company PDF profile, dynamically rendered from a PostgreSQL database.

## Tech Stack
- **Frontend**: React + TypeScript + Vite + Tailwind CSS + Framer Motion
- **Backend**: Express.js + TypeScript
- **Database**: PostgreSQL (Neon) via Drizzle ORM
- **UI Components**: shadcn/ui

## Design
- Dark charcoal/black base (#121212) with warm gold (#C9A84C) accents
- Fonts: Playfair Display (headings), DM Sans (body)
- Corporate, premium, authoritative tone
- Minimal decorative elements, strong typography hierarchy

## Page Structure
### Home Page (single-page, smooth scroll)
1. **Navbar** — Fixed top, logo + nav links (Home, About, Services, Projects, Contact) + CTA
2. **Hero** — Full viewport, headline + dual CTAs
3. **About** — Company overview + strength cards (Financial, Experience, Quality & Safety)
4. **Services** — Two categories: Core Subcontracting (8 services) + Renovation & Maintenance (12 services)
5. **Capabilities** — 6 capability blocks in grid
6. **Why Choose Us** — 6 differentiators with icons
7. **Clients** — Clean grid of 13 client company names
8. **Projects** — Featured project + full card grid from database (28 projects total)
9. **Health & Safety** — Commitment statement + stats
10. **Areas Served** — 5 Auckland regions
11. **Contact** — Tender enquiry form (name, company, email, phone, project type, message)
12. **Footer** — Corporate footer

### Project Detail Page (`/projects/:id`)
- Two-row layout: Image + Overview on top, Scope of Work + Details Grid on bottom
- Back navigation to all projects
- Category/status badges, scope bullet list, detail grid with icons

## Data Model
- `contact_messages` table: id, name, company, email, phone, projectType, message, createdAt
- `projects` table: id, client, projectName, location, scale, scopeOfWork, category, status, description, image

## API Routes
- `POST /api/contact` — Submit contact form
- `GET /api/projects` — List all projects
- `GET /api/projects/:id` — Get single project

## Key Files
- `shared/schema.ts` — Drizzle schema + Zod validation (contactMessages + projects tables)
- `shared/routes.ts` — API contract definitions
- `server/routes.ts` — Express route handlers + project seed function
- `server/storage.ts` — Database storage layer (IStorage interface)
- `client/src/App.tsx` — Router (Home + ProjectDetail + NotFound routes)
- `client/src/pages/Home.tsx` — Main home page component
- `client/src/pages/ProjectDetail.tsx` — Dynamic project detail page
- `client/src/components/sections/` — All section components (About, Services, Clients, Projects, etc.)
- `client/src/components/layout/` — Navbar, Footer
- `client/src/hooks/use-contact.ts` — Contact form mutation hook
- `client/public/images/` — 32 project images extracted from PDF (project-000.jpg to project-031.jpg)

## Project Images
Images extracted from the Crown Interiors company profile PDF using `pdfimages`. First 3 (000-002) are banners/headers. Images 003-031 are mapped to specific projects based on PDF page order.
