# Personal Website Plan: Astro + GitHub Pages

## Context

Migrating hethav.com off Replit onto GitHub Pages using Astro. The goal is a dark, modern, super-minimal single-page site with visual elements (icons over text). Top section has bio + social icon links; scrolling reveals work experience and projects.

## Stack

- **Framework:** Astro (static output)
- **Styling:** Tailwind CSS (utility-first, dark theme)
- **Icons:** Raw inline SVGs (from Simple Icons / Lucide, using `currentColor`)
- **Font:** Inter via Google Fonts
- **Hosting:** GitHub Pages via GitHub Actions

## Site Structure (single scroll page)

1. **Hero** — Name, one-line bio, row of social icon links (GitHub, LinkedIn, X, Email — icons only, no text)
2. **Experience** — Section heading + vertical list of job cards (company, role, period, description)
3. **Projects** — Section heading + 2-col grid of project cards (name, description, tags, link)

## File Structure

```
astro.config.mjs
tailwind.config.mjs
src/
  layouts/Layout.astro          # HTML shell, dark bg, fonts, meta
  pages/index.astro             # Single page composing all sections
  components/
    Hero.astro                  # Name, bio, SocialIcons
    SocialIcons.astro           # Flex row of icon <a> links
    Experience.astro            # Section with ExperienceCard list
    ExperienceCard.astro        # Single job entry
    Projects.astro              # Section with ProjectCard grid
    ProjectCard.astro           # Single project entry
  content/data.ts               # All content in one file (bio, socials, experience, projects)
  icons/*.svg                   # Raw SVG files for social icons
.github/workflows/deploy.yml   # GitHub Actions → GitHub Pages
```

## Design Tokens (via Tailwind)

- Background: `bg-neutral-950` | Cards: `bg-neutral-900/50 border-neutral-800`
- Text: `text-neutral-100` | Muted: `text-neutral-400`
- Hover accent: `text-white` or `text-sky-400`
- Spacing: `py-24`–`py-32` between sections
- Cards: `rounded-xl p-6`, subtle hover transitions

## Implementation Steps

1. **Init project** — `npm create astro@latest .`, add Tailwind, verify `npm run dev`
2. **Layout + dark theme** — `Layout.astro` with dark bg, Inter font, meta tags
3. **Hero section** — `Hero.astro` + `SocialIcons.astro` with icon SVGs
4. **Experience section** — `Experience.astro` + `ExperienceCard.astro`, placeholder data
5. **Projects section** — `Projects.astro` + `ProjectCard.astro`, placeholder data
6. **Content** — Fill `data.ts` with real info
7. **Polish** — Responsive checks, smooth scroll, hover transitions
8. **Deploy** — GitHub Actions workflow, push, enable Pages

## Verification

- `npm run dev` — preview locally at localhost:4321
- `npm run build` — confirm static output in `dist/`
- Check mobile responsiveness in browser dev tools
- Push to GitHub, confirm Actions workflow runs and site deploys
