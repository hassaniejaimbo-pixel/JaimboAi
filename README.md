# JaimboAi

## Dependency installation

This repository uses npm. Install the dependencies with `npm ci`; the committed
`package-lock.json` keeps dependency resolution reproducible on Netlify.

The standalone repository does not include a pnpm workspace catalog. Dependencies
therefore use npm-compatible versions rather than `catalog:` or `workspace:`
references. The unused `@workspace/api-client-react` dependency was removed because
its workspace package is absent and the checked-in source does not import it.

## Application startup

`vite.config.ts` configures React, Tailwind CSS, and the `@/` source alias.
`index.html` loads `src/main.tsx`, which mounts the application with the existing
error boundary and global styles. Netlify's existing `npm run build` command and
`dist` publish directory remain unchanged.

Only the not-found page was included in the original checkout, so the entry point
currently renders that existing fallback. Restore the original application pages
and routing to serve the intended application; this build repair does not recreate
missing product features.

The separate `typecheck` script still requires the original `tsconfig.json` and a
TypeScript compiler, neither of which was included in the checkout.
