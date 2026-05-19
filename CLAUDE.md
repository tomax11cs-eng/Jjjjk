# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

A single-page CZK → EUR currency converter. The whole app lives in `index.html` — markup, styles, and logic are inlined; there is no build step, no package manager, and no backend.

## Running it

Open `index.html` in a browser. There is no dev server, no `npm`, no tests. Any static host (GitHub Pages, Netlify, etc.) works as deployment.

## Architecture notes

- **Exchange rate source:** the page fetches `https://api.frankfurter.app/latest?from=CZK&to=EUR` on load. Frankfurter mirrors ECB reference rates and updates on business days (~16:00 CET). It is free, keyless, and CORS-enabled — do not swap it for an API that requires a key without first asking the user.
- **Two-way binding:** both input fields (`#czk`, `#eur`) edit the same conceptual amount. A `direction` flag tracks which side the user is currently typing in, so `recalculate()` knows whether to multiply by `rate` or divide.
- **Offline behavior:** once the rate is fetched, conversions work without network. There is no caching of the rate across reloads — a fresh fetch happens every page load, which is also how the "daily updated" guarantee is satisfied.

## Conventions

- UI strings are in Slovak. Keep them in Slovak unless the user asks for another language.
- Keep the app a single self-contained file unless complexity genuinely demands splitting it. Do not introduce a framework, bundler, or package.json without being asked.
