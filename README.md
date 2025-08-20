
# Haikus for Codespaces (Express + EJS)

A tiny Node.js web app that serves a gallery of haikus with images using Express and EJS. Originally based on the Azure Node sample and adapted for Codespaces demos.

## Tech stack
- Node.js + Express
- EJS view engine
- Static assets served from `public/`

## Quick start
Prerequisites: Node.js 18+ and npm

```bash
npm install

# Development (auto-reload)
npm run dev

# Production-like run
npm start
```

The app listens on `PORT` (environment variable) or defaults to `3000`.

Open: `http://localhost:3000`

## Available scripts
- `npm start`: Runs `node index.js`
- `npm run dev`: Runs `nodemon` for autoreload during development

## Project structure
```
index.js               # Express app entrypoint
haikus.json            # Data source for haiku text + image filename
views/index.ejs        # EJS template rendering the haiku list
public/css/main.css    # Styles
public/images/*        # Images referenced by haikus.json
process.json           # PM2 process configuration (optional)
web.config             # IIS/iisnode rewrite/handler config (Azure Windows)
package.json           # Dependencies and scripts
```

## Configuration
- `PORT`: Port to bind the HTTP server (default: `3000`).

Static files are served from `public/`. The EJS template reads from `haikus.json` via `index.js` and renders the list at the root route.

## Endpoints
- `GET /`: Renders `views/index.ejs` with `haikus.json` data
- Static: `/css/*`, `/images/*`

## Deployment
### PM2 (Linux)
```bash
npm install --production
pm2 start process.json
pm2 status
pm2 logs
```

### Azure App Service (Windows, iisnode)
`web.config` configures iisnode to route requests to `index.js` and serve static files from `public/`. Deploy the contents of this repo to your App Service; no extra build step is required beyond `npm install`.

## Codespaces
This repo works out-of-the-box in GitHub Codespaces. See the [Codespaces quickstart](https://docs.github.com/en/codespaces/getting-started/quickstart) for a guided tour.

## License
MIT — see `LICENSE`.
