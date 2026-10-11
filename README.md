# BizPilot AI — Frontend Learning Starter

A professional, responsive HTML/CSS/JavaScript workspace for business productivity workflows, prepared for Davine Technologies. The project runs locally without a paid service or API key.

## Current implementation

- Dashboard with actual local activity and quick actions
- AI Writing Studio: demo email drafting, rewriting, and executive-summary patterns
- Business report, meeting summary, and research-summary demo tools
- Action-item list with manual creation, extraction review, status changes, deletion, and browser persistence
- Reusable Prompt Library
- End-to-end workflow: meeting notes → editable summary → action-item extraction → editable follow-up email
- Activity history and preferences stored in browser localStorage
- Copy and text-download actions for generated drafts
- Responsive desktop, tablet, and mobile layouts

## Important: Demo Mode

This is a **frontend-only** implementation. The generator in `js/generator.js` uses deterministic local logic and simple text patterns. It is not a live generative AI model. Outputs are clearly labelled as demo outputs and may need substantial review. There is no backend, authentication, external AI provider, live web research, or server-side persistence.

Do not enter confidential or sensitive information. Browser localStorage is not a secure multi-user data store.

## Run locally

Option 1: Open `index.html` directly in a modern browser.

Option 2: use Python's local static server:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>.

No package installation is required. The Google Fonts link is optional; the application falls back to system fonts if the network is unavailable.

## Project structure

```text
bizpilot-ai/
├── index.html
├── styles.css
├── app.js
├── js/
│   ├── generator.js
│   └── prompts.js
└── README.md
```

- `index.html`: application shell, sidebar navigation, top bar, footer
- `styles.css`: design tokens, layout, components, responsive rules
- `app.js`: navigation, page views, forms, browser storage, workflow orchestration, copy/download interactions
- `js/prompts.js`: reusable prompt template catalogue
- `js/generator.js`: deterministic demo generation functions

## Local data

Action items, preferences, and optional activity history use browser `localStorage`. Activity history stores task labels, execution mode, status, and timestamps; it does not store source text. Use **Settings → Clear data** to remove locally stored BizPilot data. Browser privacy settings or clearing site data may also remove it.

## Extending with a real model

For a real AI provider, add a backend service and keep credentials in server-side environment variables. Never place secret keys in `app.js`, `generator.js`, browser storage, or a public repository. Replace the demo generator with a request to a validated backend endpoint. Add input limits, timeouts, provider error handling, structured response validation, privacy-conscious logs, and tests. Keep a human review step before any external action.

## Tests and verification

No build system or test runner is required. Basic source checks can be run with:

```bash
node --check app.js
node --check js/generator.js
node --check js/prompts.js
```

Manual smoke test checklist:

1. Open the app and navigate through all sidebar items.
2. Generate a demo email, report, meeting summary, and research summary.
3. Confirm empty required inputs show an error.
4. Copy or download a draft.
5. Add an action item, mark it complete, filter, and delete it.
6. Extract action items from notes and review them before saving.
7. Complete all three workflow stages and edit the summary and email.
8. Change settings and reload to confirm local preferences persist.
9. Clear activity and all local data.
10. Resize the browser to mobile width and verify navigation and forms remain usable.

## Known limitations

- No live model integration, local-model adapter, backend, database, login, or multi-user support.
- Action extraction is rule-based and can miss tasks or misinterpret language.
- Demo summaries do not guarantee factual completeness.
- No live internet research, source citations, email delivery, publishing, or external task creation.
- Browser-local storage is best suited to demonstrations, not production records.


## Branding asset

The sidebar uses `bizpilot-logo.png`. Keep this image in the same folder as `index.html` so the logo loads correctly when you run or deploy the site.
