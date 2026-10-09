# E-commerce Customer Intelligence Dashboard

Single-file, client-side BI dashboard (HTML + CSS + JS, Chart.js 4.4.1 from cdnjs). Ships with a **synthetic** dataset (seeded generator, no real company). All processing stays in the browser.

## Files
- `index.html` – the full app (UI, calculations, sample-data generator)
- `sample_orders.csv` – the same synthetic data, usable as an upload template
- `README.md` – this file

## Run locally
1. Put the files in one folder.
2. Open `index.html` in a browser (internet needed once for Chart.js), or serve it: `python3 -m http.server 8000` then visit http://localhost:8000.

## Publish on GitHub Pages
1. Create a GitHub repo and push the three files to the `main` branch (`index.html` at repo root).
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
3. After a minute the site is live at `https://<username>.github.io/<repo>/`.

## CSV format
Required: `order_id, order_date (YYYY-MM-DD), customer_id, region, category, product, quantity (int > 0), unit_price (≥0), unit_cost (≥0)`. Optional: `discount` (0–1, blank = 0). One row per order line. Invalid rows are skipped and reported; missing required columns reject the file and keep current data.

## Metrics & caveats
See the Methodology section inside the dashboard. Insights are rule-based descriptions, not forecasts.

## Tests run
A Node script exercised the core logic: CSV parsing (quotes/CRLF), validation of bad rows, revenue/profit math, that region/category/segment/month breakdowns each sum to the totals, filter correctness and empty results, cohort M0 = 100%, and export → re-import round-trip.
