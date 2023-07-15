# Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Setup

Make sure to install the dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm run dev

# yarn
yarn dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm run build

# yarn
yarn build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm run preview

# yarn
yarn preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.


# Updating Node Packages Windows, MacOS with Docker:
When working with MacOS or Windows the Nuxt3 packages for Esbuild require a specific linux version of the package when running inside docker.

If not running linux, decide whether to work with docker here or on the local machine, if working with docker on Windows or MacOS:

Do not locally install the node_modules locally. If you need to add a module, add it to the section of the package.json you need, clear the volumes the the comand listed below this and then rebuild the container.

# Clear All Docker Volumes:
docker volume rm $(docker volume ls -q)

# Rebuild container
docker-compose build --no-cache

# Bring Up the container
docker-compose up -d

# npm run dev - Command within Docker
docker-compose run --rm frontend npm run dev


