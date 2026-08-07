# Running the Module 1 Presentation

## Prerequisites

- Node.js 18 or newer
- npm

## Start the presentation

```bash
npm install
npm run dev
```

Slidev opens the presentation in a browser. If it does not open automatically, use the local URL printed in the terminal, normally `http://localhost:3030`.

## Present

- Use the arrow keys or Space to navigate.
- Press `O` for the slide overview.
- Press `P` to open Presenter Mode with speaker notes and a timer.
- Press `F` for fullscreen.

## Build or export

```bash
npm run build
npm run export
```

The production site is written to `dist/`. PDF export may ask Slidev to install Playwright on first use.

## Edit content

- Presentation entry point: `slides.md`
- Shared styling: `style.css`
- Topic content: `Agenda/Module 1 - Responsible AI for Software Engineering/*.md`
- Company policy link: replace `COMPANY_AI_POLICY_URL` in `02-company-ai-usage-policy.md`
