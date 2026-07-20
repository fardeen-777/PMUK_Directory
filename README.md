# PMUK Staff Phone Directory

A single-page, searchable phone directory for PMUK staff — 559 numbers combined
from the Region & Area Office mobile bill and the Bundle-17 Branch Manager list.
No backend, no build step — it's one self-contained `index.html` file.

## Put it on GitHub Pages (5 minutes)

1. **Create a new repo** on GitHub — e.g. `PMUK-Staff-Directory`. Public repo
   (Pages on a free GitHub account only serves public repos).
2. **Upload `index.html`** — on the repo page, click **Add file → Upload files**,
   drag `index.html` in, then **Commit changes**. (No need to touch `README.md`,
   it's just documentation — GitHub Pages ignores it.)
3. **Turn on Pages** — go to **Settings → Pages**. Under "Build and deployment",
   set **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**.
   Click **Save**.
4. **Wait ~1 minute**, then refresh that same Settings → Pages screen — GitHub
   will show the live URL, something like:
   `https://<your-username>.github.io/PMUK-Staff-Directory/`
5. Open that link. That's the directory — bookmark it on your phone for
   one-tap lookups in the field.

## Updating the numbers later

The data lives inline inside `index.html` (search for `const DATA =` near the
bottom of the file) — there's no separate database or spreadsheet it reads
from. To refresh it:

- Ask Claude to regenerate `index.html` from the latest mobile bill / bundle
  files, then re-upload it here (same **Add file → Upload files** step,
  GitHub will ask to replace the existing file).
- Or hand-edit the `DATA` array directly if it's a small tweak (one JSON
  object per person — `name`, `designation`, `location`, `category`,
  `mobile`, `pin`, `remarks`).

## What's in here

- `index.html` — the whole app: markup, styles, data, and search logic in one file.
- `README.md` — this file.

## Notes on the data

- Branch Manager entries (397 of them) have no branch name in the source
  file, so they're labeled Branch 1–397 in original list order.
- "Office Code (PIN)" is from the source file and is **not** a unique
  personal ID — a few codes repeat across two staff at the same office.
- Numbers are for internal PMUK use.
