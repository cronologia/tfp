# AGENTS.md

Operating guide for AI coding agents (and humans) working in this repository.
Read this and `context.md` before making changes. The shared method lives in
`cronologia/core` (skills: sourcing-rules, bootstrap-project, mine-video,
dossier-research); the architecture rationale in `cronologia/fsp` → `docs/adrs/`.

## What this project is

A compiled static website documenting the chronology of the **TFP**
(Tradição, Família e Propriedade) and of Plinio Corrêa de Oliveira.
A single JSON file is the source of truth; a zero-dependency Node script
compiles it into static HTML served by GitHub Pages.

## Repository map

```
data/chronology.json     SOURCE OF TRUTH — facts, events, figures, organizations, references (hand-edited)
src/styles.css           Stylesheet (copied into the build)
scripts/validate-data.js Schema check (runs in CI before the build)
build.js                 Compiler: data/chronology.json -> docs/
test/                    node:test suites (helpers + data invariants + drift check)
.github/workflows/deploy.yml  CI: validate, test, build, drift check, Pages deploy (main + manual dispatch)
docs/                    COMPILED OUTPUT, served by GitHub Pages (committed)
```

## Working agreements

1. **Edit data, not output.** Change `data/chronology.json`, run
   `node build.js`, commit the regenerated `docs/` in the same change.
2. **Keep the build green.** `node scripts/validate-data.js`, `node --test`
   and `node build.js` must all pass; CI fails if `docs/` drifts.
3. **Cite every fact; flag every uncertainty; attribute every contested
   characterization.** The validator enforces non-empty `sources[]`.
4. **A merged PR is finished** — branch fresh from `main` for new work.

## Data quality & sourcing rules

Beyond the family's five core rules: four source families, always labeled
(movement/sympathetic — IPCO, tfp.org, arautos.org, pliniocorreadeoliveira.info;
ecclesiastical — CNBB, Vatican; academic — Zanotto, Caldeira, CPDOC-FGV;
critical/press/ex-member); campaign numbers are the movement's own —
"according to the TFP"; 'sect' accusations are attributed accusations with
the movement's replies, never asserted; keep TFP ≠ SSPX straight (lay vs
priestly; Castro Mayer is the bridge — cross-link fsspx); the Heralds/IPCO
split is presented symmetrically; 'Counter-Revolution' is Plinio's technical
term, attributed to the 1959 text; do not present Centro Dom Bosco as a TFP
entity.
