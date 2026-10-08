# CookieLife — Little Log

A mobile-first newborn tracker: feeds (breastfeeding L/R timer, bottle amounts in
ml/oz, solids), diapers (wet/dirty/both/dry) and sleep (timer or manual), with a
Today dashboard, History and 7/14/30-day Trends charts.

**Live app:** https://dannygelman95.github.io/CookieLife/

`index.html` is the whole app — no build step. Open it directly or add the live
URL to your phone's home screen.

## Where the data is saved

Every entry is saved in the browser on the device (`localStorage`), and — once
**Settings → Cloud sync · GitHub** is connected — in a JSON file in a private
GitHub repo (default `DannyGelman95/CookieLife-data`, file `littlelog.json`).

- Changes upload a few seconds after logging; other devices pull every minute and
  whenever the app is reopened. Each upload is a commit, so the repo history is a
  full version history of the log.
- Devices merge by entry (newest edit wins, deletions are remembered), so both
  parents can log at the same time. Running feed/sleep timers sync too.
- Works offline; it syncs when the connection is back.

Setup (once):
1. Create a **private** repo, e.g. `CookieLife-data` (keep it private — this repo,
   `CookieLife`, is public).
2. Create a token: open
   https://github.com/settings/tokens/new?scopes=repo&description=Little%20Log
   (the app's Settings → Cloud sync has the same link), set Expiration to
   *No expiration*, tap **Generate token** and copy the `ghp_…` code.
   A fine-grained token with Contents: Read and write on the data repo also works.
3. In the app: Settings → Cloud sync → paste the token → **Connect & sync**. Do
   the same on each phone.

The token is stored only in that browser and only sent to `api.github.com`.

Every push to `main` redeploys via `.github/workflows/pages.yml`.
