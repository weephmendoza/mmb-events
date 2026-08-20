## Base44 dev environment

Run the app with Docker Compose (no local Node install needed):

```
docker compose -f docker-compose.base44.yml up -d
```

- Single static Astro site (mmb-events). No backend, database, or external services — no secrets required.
- Runs from bind-mounted source on `node:22`; `npm install` runs at container start, then `astro dev --host 0.0.0.0 --port 4321`.
- Host port 3000 → container 4321. Live reload is on (Vite file watcher).
- `astro.config.mjs` sets `vite.server.allowedHosts: true` so the preview's external hostname is accepted (Vite otherwise 403s unknown Host headers).
- Verify: `curl -sf -H "Host: external-preview.example.com" http://localhost:3000/` → 200.

## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
