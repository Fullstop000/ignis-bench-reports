# ignis · benchmark reports

Static-hosted per-run HTML reports for [ignis](https://github.com/Fullstop000/ignis)
against agent benchmarks (Terminal-Bench 2.x today, others later).

The canonical history lives in the main repo's
[`benchmarks/RESULTS.md`](https://github.com/Fullstop000/ignis/blob/master/benchmarks/RESULTS.md).
Each row links here for the per-trial drill-in. This repo is just the static
host — no scripts, no run output, just rendered HTML.

## Layout

```
.
├── index.html              # landing page with the run list
├── reports/                # one HTML per run; filename matches the history/ CSV stem
│   └── tb21-minimax-m3-20260602.html
└── README.md
```

## Adding a new run

1. Generate the HTML in the main repo:
   ```bash
   cd benchmarks/terminal-bench
   python3 scripts/generate_report.py runs/<job-dir> -o /tmp/<run-slug>.html
   ```
2. Copy `<run-slug>.html` to `reports/` here, mirroring the CSV name committed
   under `benchmarks/terminal-bench/history/` in the main repo.
3. Add one `<tr>` to `index.html` (newest first) and update the row in
   `benchmarks/RESULTS.md` to link the new HTML.
4. Push — Vercel auto-deploys.

## Hosting

Deployed on Vercel as a static site (no build step, no framework). The
`vercel.json` enables `cleanUrls` so reports work as `/reports/<slug>`
without the `.html` suffix in the URL.

## License

Apache-2.0, same as the main repo.
