# Real Estate Marketing Director Suite (Offline)

This repository contains an offline-ready landing page / single-file application for the "Real Estate Marketing Director Suite" — an AI-assisted set of tools for real-estate marketing workflows (strategy, content, social, reports, task manager and more).

## What I changed
- Removed embedded sensitive tokens and replaced them with placeholders in `index.html`.
- Added this README and a `.gitignore` and a GitHub Actions workflow to help publish to GitHub Pages.

## Preview locally
1. Clone the repository:

   git clone https://github.com/IslamAbu-hares/Real_Estate_Marketing_Suite_Offline.git
   cd Real_Estate_Marketing_Suite_Offline

2. Serve the folder with a static server and open `index.html` in a browser:

   # using Python 3
   python -m http.server 8000

   # or with npm http-server
   npx http-server .

3. Open http://localhost:8000 in your browser.

## Runtime secrets & how to inject them
For security, the following values were removed from `index.html` and replaced with placeholders:

- Firebase config & token
- Any inlined JWT/API tokens

How to provide them at runtime:
- Option A (recommended): Set them in a small wrapper script or server that injects values at runtime from environment variables.
- Option B: In local testing, edit `index.html` and replace the placeholder strings (`__FIREBASE_CONFIG_PLACEHOLDER__`, `__INITIAL_AUTH_TOKEN_PLACEHOLDER__`, `__APP_ID_PLACEHOLDER__`) with your values. Do NOT commit secrets to this repo.
- Option C: Use GitHub Actions secrets and a CI job that writes a sanitized `index.html` at build time (not stored in source).

## GitHub Pages
A GitHub Actions workflow was added at `.github/workflows/pages.yml` to publish the repository as a Pages site on push to `main`.
After enabling the workflow, enable GitHub Pages in repository Settings → Pages and select the `gh-pages` workflow output (or follow the Actions output to finish setup).

Note: You may need to authorize the repository and enable Pages in the Settings UI.

## Security notes
- Never commit API keys or long-lived tokens to the repository. Use environment variables, secrets manager, or GitHub Secrets used only by Actions.
- If the removed Firebase/JWT values are active credentials, consider revoking/rotating them.

## Next steps I can take for you
- Wire a build step that injects secrets from GitHub Secrets (via Actions) and publishes safely.
- Add more instructions and screenshots.
- Revert to a placeholder template that loads runtime config from `/config.json` (served by your backend).

If you want me to proceed with any of the actions above, tell me which one.
