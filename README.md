# TFP — Cronologia

A compiled static website documenting the chronology of the **TFP**
(Sociedade Brasileira de Defesa da Tradição, Família e Propriedade, founded
1960) and its founder **Plinio Corrêa de Oliveira**: the campaigns, the
international network, the 1985 CNBB note, the post-1995 succession dispute,
and the two branches of today — the Heralds of the Gospel and the IPCO.

Part of the [Cronologia](https://cronologia.github.io) family; built from the
[`core`](https://github.com/cronologia/core) template. Single JSON source of
truth (`data/chronology.json`), zero-dependency build, GitHub Pages.

```bash
node scripts/validate-data.js && node --test && node build.js
```

Publish: Settings → Pages → GitHub Actions + Actions variable
`ENABLE_PAGES=true` (with `main` as default).
