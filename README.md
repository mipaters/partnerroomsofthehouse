# Rooms of the Partner

Interactive demo for Northbridge Technology Solutions (illustrative data only). Plain HTML/CSS/JS, no build step.

## Layout

```
src/
  index.html               page shell
  css/styles.css           styles
  js/app.js                data (ROOMS etc.), rendering, walkthrough
  staticwebapp.config.json Azure Static Web Apps config
.github/workflows/         deploy pipeline
```

## Run locally

```
npx serve src
```

(or open `src/index.html` directly)

## Deploy to Azure Static Web Apps

1. Push this repo to GitHub.
2. In the Azure portal: Create a resource > Static Web App, Plan: Free, Source: GitHub, pick this repo and `main`.
3. Build preset: Custom. App location: `src`. API location: empty. Output location: empty.
4. Azure adds the `AZURE_STATIC_WEB_APPS_API_TOKEN` secret to the repo. If it generates its own workflow file, delete it and keep `.github/workflows/azure-static-web-apps.yml` (or copy the generated secret name into it).

Every push to `main` deploys; pull requests get preview environments.

## Growing it

- Split `app.js` into ES modules (`<script type="module">`) as it grows; inline `onclick` handlers will then need to be attached via `addEventListener` or exposed on `window`.
- Move the `ROOMS` data to JSON under `src/data/` and `fetch` it.
- Add an `src/images/` folder for assets.
