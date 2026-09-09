# Repository Guidelines

## Project Structure & Module Organization

- `src/pages/` contains Astro routes, including posts, archives, tags, categories, RSS, and robots endpoints.
- `src/components/` and `src/layouts/` contain reusable Astro/Svelte UI and page shells; shared behavior belongs in `src/utils/`, `src/plugins/`, or `src/types/`.
- Markdown content lives in `src/contents/posts/` and `src/contents/specs/`. Follow the post schema in `src/content.config.ts` for frontmatter.
- Global CSS is in `src/styles/`; translations are in `src/locales/`; static files belong in `public/`.
- Root configuration files include `yukina.config.ts`, `astro.config.mjs`, `tailwind.config.mjs`, and `svelte.config.js`.

## Build, Test, and Development Commands

Use Node.js 22 or newer and pnpm (the repository pins pnpm 9.15.4 through Corepack).

```bash
corepack enable
pnpm install       # Install dependencies
pnpm dev           # Start the Astro development server
pnpm astro check   # Run Astro/TypeScript diagnostics
pnpm build         # Build the site and generate the Pagefind index
pnpm preview       # Serve the production build locally
```

## Coding Style & Naming Conventions

Use two-space indentation, semicolons, double-quoted strings, and TypeScript types for public data structures. Run Prettier before submitting changes; the repository uses `prettier-plugin-astro` and `prettier-plugin-tailwindcss`.

Use PascalCase for reusable component filenames (for example, `PostCard.astro`), lowercase names for utilities and route files, and descriptive camelCase for variables and functions. Keep Tailwind classes in the order produced by Prettier.

## Testing Guidelines

No automated test framework or coverage threshold is configured. For every change, run `pnpm astro check` and `pnpm build`; for UI changes, also verify affected routes with `pnpm dev` at desktop and mobile widths. If adding tests, place them beside the feature or in a clearly named test directory and document the command in `package.json`.

## Commit & Pull Request Guidelines

Recent commits use short, imperative prefixes such as `Feat:`, `Fix:`, and `Chore:` (for example, `Fix: improve category rendering`). Keep each commit focused. Pull requests should explain the user-visible impact, list validation commands, link any related issue, and include screenshots or recordings for visual changes. Call out configuration or content migrations explicitly.

## Security & Configuration Tips

Do not commit `.env` files, credentials, or generated `dist/` and `.astro/` output. Review external image and link URLs added to `yukina.config.ts` or Markdown content before merging.
