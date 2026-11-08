# Architecture

## What this is

Open-Source API Development Ecosystem • https://hoppscotch. Open source API development ecosystem. The repository is a Node project. This repository is a fork.

## Layout

- `packages/` — `codemirror-lang-graphql`, `hoppscotch-agent`, `hoppscotch-backend`, `hoppscotch-cli`, `hoppscotch-common`, `hoppscotch-data`, `hoppscotch-desktop`, `hoppscotch-js-sandbox` (+4 more)
- Tooling: `.devcontainer`, `.github`, `.husky`, `.dockerignore`, `.editorconfig`, `.env.example`, `.envrc`, `.firebaserc`…
- Root files: `aio-multiport-setup.Caddyfile`, `aio-subpath-access.Caddyfile`, `aio_run.mjs`, `CHANGELOG.md`, `CODE_OF_CONDUCT.md`, `CODEOWNERS`, `commitlint.config.js`, `CONTRIBUTING.md`, `devenv.lock`, `devenv.nix`, `devenv.yaml`, `docker-compose.deploy.yml`, `docker-compose.yml`, `firebase.json`, and 14 more files

## How the pieces fit

Node project declared by the root `package.json`. `docker-compose.yml` names images `postgres:15`. `packages/` contains `codemirror-lang-graphql`, `hoppscotch-agent`, `hoppscotch-backend`, `hoppscotch-cli`, `hoppscotch-common`, `hoppscotch-data`, `hoppscotch-desktop`, `hoppscotch-js-sandbox`, `hoppscotch-kernel`, `hoppscotch-relay`.

## How to run

Scripts in the root `package.json`:

- `dev` — `pnpm -r do-dev`
- `start` — `http-server packages/hoppscotch-selfhost-web/dist -p 3000`
- `lint` — `pnpm -r do-lint`
- `test` — `pnpm -r do-test`

Scripts in `packages/hoppscotch-agent/package.json`:

- `dev` — `vite`
- `build` — `vue-tsc --noEmit && vite build`
- `preview` — `vite preview`
- `lint` — `eslint src`

Scripts in `packages/hoppscotch-backend/package.json`:

- `build` — `nest build`
- `start` — `nest start`
- `lint` — `eslint "{src,apps,libs,test}/**/*.ts" --fix`
- `test` — `jest`

Scripts in `packages/hoppscotch-cli/package.json`:

- `build` — `pnpm exec tsup`
- `dev` — `pnpm exec tsup --watch`
- `test` — `pnpm run build && vitest run`

## External services named in the repo

- Firebase — `firebase.json`
- PostgreSQL — `pg` in packages/hoppscotch-backend/package.json
