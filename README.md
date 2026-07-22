# PMUK Staff Phone Directory

A single-page, searchable phone directory for PMUK staff — 3,704 employees
combined from the Zone & Area Office mobile bill and 19 zone-level branch-staff
rosters (CM, ABM, Branch Manager, through to Zonal Manager). No backend, no
build step — it's one self-contained `index.html` file.

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

- Branch-level staff (CM, ABM, Branch Manager, Trainee) come from 19 zone
  mobile-bill files. Designation text was wildly inconsistent at source
  (140+ spelling variants of the same ~9 roles), so each entry also gets a
  normalized **Role Group** — the original raw text is kept alongside it,
  never discarded.
- A legacy anonymous "Branch Manager" list (397 entries, no names) has been
  retired in favor of the named zone rosters above, which already covered
  392 of those same numbers. The 5 that didn't match anything current are
  kept at the bottom of Branch Staff, flagged as unmatched.
- "Zone & Area Office" covers Zonal/Regional Managers, Area Managers,
  HR & Admin, Finance & Accounts, and Drivers.
- Every entry has a Directory ID (0001–3704) you can search by directly.
- Numbers are for internal PMUK use.
