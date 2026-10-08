# CookieLife — Little Log

A mobile-first newborn tracker: feeds (breastfeeding L/R timer, bottle amounts in
ml/oz, solids), diapers (wet/dirty/both/dry) and sleep (timer or manual), with a
Today dashboard, History and 7/14/30-day Trends charts.

**Live app:** https://dannygelman95.github.io/CookieLife/

`index.html` is the whole app — no build step, no network calls. Open it directly
or add the live URL to your phone's home screen. Data is stored in the browser
(`localStorage`) on that device; use Settings → Export/Import backup to move it.

Every push to `main` redeploys via `.github/workflows/pages.yml`.
