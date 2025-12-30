# Coaching Tony Stark Documentation

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

## Installation

### Using pnpm (Recommended)

```bash
# Install dependencies
pnpm install

# Build native modules (required for sharp image processing)
cd node_modules/.pnpm/sharp@0.32.6/node_modules/sharp && npm run install
cd ../../../../../
```

### Using yarn

```bash
yarn
```

## Local Development

### Using pnpm

```bash
pnpm start
```

### Using yarn

```bash
yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

## Build

### Using pnpm

```bash
pnpm build
```

### Using yarn

```bash
yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

## Deployment

### Using pnpm

Using SSH:

```bash
USE_SSH=true pnpm deploy
```

Not using SSH:

```bash
GIT_USER=<Your GitHub username> pnpm deploy
```

### Using yarn

Using SSH:

```bash
USE_SSH=true yarn deploy
```

Not using SSH:

```bash
GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.

## Other Useful Commands

### Clear cache and generated assets

```bash
# Using pnpm
pnpm clear

# Using yarn
yarn clear
```

### Serve built website locally

```bash
# Using pnpm
pnpm serve

# Using yarn
yarn serve
```

### Type checking

```bash
# Using pnpm
pnpm typecheck

# Using yarn
yarn typecheck
```
