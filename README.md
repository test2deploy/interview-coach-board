# Interview Rehearsal Coach — Production Board

A single-page **release-pipeline dashboard** that tracks the build of the Interview Rehearsal Coach — a rehearsal tool for QA / DevOps engineers who interview in English as a second language.

The board shows every stage of the project as a pipeline **job**, and every task as a **check** (`passed` · `running` · `queued` · `deferred`). It reflects real production status, not a wishlist.

> **Live board:** `https://<your-username>.github.io/<your-repo>/`
> *(replace with your actual GitHub Pages URL)*

---

## What's in here

| File | Purpose |
|------|---------|
| `index.html` | The whole board — self-contained, no build step, no dependencies (fonts load from Google Fonts CDN). |

That's it. Open `index.html` in any browser to view it locally; no server needed.

---

## How to update the board

All the content lives in one place: the **`STAGES` array** near the bottom of `index.html`.

Each stage looks like this:

```js
{ id:"03·calibrate", name:"Calibration", status:"running", steps:[
  { t:"Build test set: ~5 weak + ~5 strong answers", s:"running" },
  { t:"Curate the 60-question bank",                 s:"queued"  },
]}
```

To move work forward, just change a check's `s` value:

- `s:"queued"` → `s:"running"` → `s:"passed"`

The pipeline lane, progress counts, and the "checks passed" total all **recompute automatically** — you never edit numbers by hand.

**Status values**

| Value | Meaning |
|-------|---------|
| `passed` | done ✓ |
| `running` | in progress ▶ |
| `queued` | not started ○ |
| `deferred` | post-launch ⋯ (stage-level only) |

---

## Publish on GitHub Pages

1. Make sure this repo is **Public** (Pages is free for public repos).
2. Ensure the board file is named **`index.html`** at the repo root.
3. Go to **Settings → Pages**.
4. Under *Build and deployment*: Source = **Deploy from a branch**, Branch = **main**, folder = **/ (root)**, then **Save**.
5. Wait 1–2 minutes, refresh, and copy the live URL that appears at the top.

---

## Notes

- This is a **status display**, not an interactive checklist — boxes reflect work done and are updated in the source file.
- The board is static and safe to host publicly. When the actual app is deployed later, **never commit API keys** — they belong in a secret environment variable, not in the repo.
