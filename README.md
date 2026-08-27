# tech-report

Technical reports by [Bat](https://brandeispatrick.github.io/blog/) — benchmarks run
end to end and products taken apart, with the method, the caveats, and the raw
numbers attached.

**Live:** https://brandeispatrick.github.io/tech-report/

| Report | Status | Live | Source |
|---|---|---|---|
| **Caveman vs Headroom** — which Claude Code token saver actually saves tokens, and which *kind* | results in (56 Opus runs) | [read](https://brandeispatrick.github.io/tech-report/skill-gym/) | [`skill-gym/`](skill-gym/) |
| **Devin vs Cursor** — two opposite bets on how an AI should index and retrieve a codebase | pre-test v0, evaluation not yet run | [read](https://brandeispatrick.github.io/tech-report/devin-vs-cursor/) | [`devin-vs-cursor/`](devin-vs-cursor/) |

## Layout

Each report is a directory that owns everything it needs: a self-contained
`index.html` (no build step, no shared stylesheet — fonts from Google Fonts, all
CSS and figures inline), plus whatever produced it.

```
index.html            landing page — the report index
skill-gym/
  index.html          the report
  gym.py              sandbox-isolated benchmark runner
  analyze.py          event-log → token/cost tables
  fetch_tasks.py      pins benchmark instances
  bin/                deterministic per-task gates
  tasks/              pinned SWE-bench / SpreadsheetBench instances
  results/            summary tables + results.json the page charts
  README.md           method, isolation model, how to run it
devin-vs-cursor/
  index.html          the report
  REPORT.md           the technical report in prose
  PLAN.md             evaluation design: probes, hypotheses, protocol
  research/           annotated primary-source notes with confidence tags
```

Published from `main` at the repo root via GitHub Pages, so a report at
`skill-gym/index.html` is served at `/tech-report/skill-gym/`. `.nojekyll` keeps
Pages from touching the files.

## Add a report

1. Create `your-slug/index.html`. Copying an existing report is the fastest start —
   they share one design system (paper `#F7F6F5`, Source Serif 4 / Inter / Geist Mono,
   200px sidebar + article grid) and differ only in `--accent`.
2. Keep the sidebar's `&larr; All reports` back-link pointing at `../`.
3. Add a `<a class="card">` entry to the root `index.html`, setting `--ac` inline to
   the report's accent so the card matches the page it opens.
4. Add a row to the table above, and link it from the blog if it is worth reading.

## History

This repo is the merge of two previously separate repos, `devin-vs-cursor` and
`skill-gym`, brought in with `git subtree` — their full commit history is preserved
under the respective prefixes.
