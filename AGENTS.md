# Agent Instructions — nextjs-16-starter-tailwind

Next.js 16 starter template with React 19, TypeScript 5, Tailwind CSS 4, and dark/light/system theme support.

## Build & Dev Commands

| Task                   | Command         |
| ---------------------- | --------------- |
| Dev server (Turbopack) | `pnpm dev`      |
| Production build       | `pnpm build`    |
| Start production       | `pnpm start`    |
| Lint                   | `pnpm lint`     |
| Lint + auto-fix        | `pnpm lint:fix` |
| Format                 | `pnpm format`   |

> Preferred package manager is **pnpm** (see `pnpm-workspace.yaml`).

## Project Structure

- `src/app/` — Next.js App Router root
- `src/app/layout.tsx` — Root layout; wraps children in `ThemeProvider` from `next-themes`
- `src/app/globals.css` — Tailwind v4 import + dark mode custom variant (`@custom-variant dark`)
- `src/app/(delete-this-and-modify-page.tsx)/` — Example components to reference/delete when scaffolding; not a real route (route group used as a hint to consumers)
- `public/images/` — Static assets

## Key Conventions

- **Path alias**: `@/` maps to `src/` (configured in `tsconfig.json`)
- **Tailwind v4**: Uses CSS-first config (`@import 'tailwindcss'`). No `tailwind.config.js`. Customise via CSS variables in `globals.css`.
- **Dark mode**: Class-based (`attribute='class'` on `ThemeProvider`). Custom variant defined as `@custom-variant dark (&:is(.dark *))`. Use `dark:` Tailwind prefix for dark-mode styles.
- **Fonts**: Local fonts loaded via `next/font/local` in `layout.tsx`; exposed as CSS variables `--font-geist-sans` / `--font-geist-mono`.
- **`suppressHydrationWarning`** on `<html>` is intentional — required by `next-themes` to avoid hydration mismatch from theme class injection.
- **Output**: `next.config.ts` sets `output: 'standalone'` for Docker deployments.
- **Turbopack**: Both `dev` and `build` scripts use `--turbopack`.

## Code Style

- ESLint 9 flat config (`eslint.config.mjs`) — includes Next.js core-web-vitals, TypeScript, Prettier compat, and Tailwind rules.
- Prettier with `@trivago/prettier-plugin-sort-imports` (auto-sorts imports) and `prettier-plugin-tailwindcss` (auto-sorts class names). Always run `pnpm format` after editing.
- Single quotes, no semicolons enforced by Prettier (check `.prettierrc` if present).

## Docker

Two Dockerfiles are provided:

- `Dockerfile` — Node.js 24 Alpine
- `Dockerfile.bun` — Bun 1.3.14 Alpine

Both expect a standalone Next.js build (`output: 'standalone'`).

## Theme System

Theme switching uses `next-themes`. See [ThemeSwitch component](<src/app/(delete-this-and-modify-page.tsx)/ThemeSwitch.tsx>) for the reference implementation pattern (mounted-guard pattern to avoid SSR flash).

## Reference

Full setup and extension recommendations: [README.md](README.md)
