# Kalkulačka CZK → EUR

Jednoduchá webová kalkulačka na prevod českých korún na eurá (a naopak). Kurz sa sťahuje z verejného API [Frankfurter](https://www.frankfurter.app), ktoré používa dáta Európskej centrálnej banky a aktualizuje sa každý pracovný deň.

## Spustenie

Stačí otvoriť `index.html` v prehliadači — žiadny build, žiadne závislosti.

```sh
# napríklad
xdg-open index.html      # Linux
open index.html          # macOS
start index.html         # Windows
```

Alebo si ju hosti ako statickú stránku (GitHub Pages, Netlify, Vercel) — všetka logika beží v prehliadači.

## Ako to funguje

Pri každom otvorení stránky sa stiahne aktuálny kurz `CZK → EUR` z `https://api.frankfurter.app/latest?from=CZK&to=EUR`. Pole CZK aj EUR sú prepojené — keď napíšeš hodnotu do jedného, druhé sa automaticky prepočíta. Tlačidlo `⇅` prehodí smer prevodu.

Internet je potrebný pri prvom načítaní (kvôli kurzu); po načítaní funguje prepočet aj offline.
