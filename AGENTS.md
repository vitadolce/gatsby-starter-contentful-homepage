# AGENTS.md

## Cursor Cloud specific instructions

### Overview

This is a **Gatsby 4 Starter Contentful Homepage** — a static site built with Gatsby that fetches content from Contentful (headless CMS) at build time. There is only one service: the Gatsby frontend dev server on port **8000**.

### Prerequisites

- **Node.js 18** is required (Gatsby 4 is incompatible with Node 22+). The default nvm alias is set to `18.20.8`.
- **Yarn** is the package manager (lockfile: `yarn.lock`).

### Environment Variables

The following secrets must be configured for the dev server and build to work:

| Variable                  | Required | Purpose                     |
| ------------------------- | -------- | --------------------------- |
| `CONTENTFUL_SPACE_ID`     | Yes      | Contentful space identifier |
| `CONTENTFUL_ACCESS_TOKEN` | Yes      | Content Delivery API key    |

These are injected as environment variables from Cursor Cloud secrets. Alternatively, create `.env.development` (see `.env.EXAMPLE`).

### Common Commands

See `package.json` scripts. Key commands:

- `yarn start` / `yarn develop` — runs `gatsby develop` on port 8000
- `yarn build` — production build
- `yarn clean` — clears Gatsby cache (run after schema changes)
- `npx prettier --check "src/**/*.{js,jsx,css.ts}"` — lint check

### Non-obvious Caveats

- There are **no automated tests** configured in this project. Prettier is the only lint tool.
- `gatsby-source-contentful` will fail immediately if `CONTENTFUL_SPACE_ID` or `CONTENTFUL_ACCESS_TOKEN` are missing or invalid. The dev server cannot start without valid Contentful API credentials.
- If you get stale data or schema errors after content model changes in Contentful, run `yarn clean` before `yarn start`.
- The setup script (`yarn setup`) is interactive (uses `inquirer`) and should not be run non-interactively by agents.
