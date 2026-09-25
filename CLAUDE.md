# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status

Early scaffold. Both apps are still the stock templates: OrderGateway serves only the sample `/weatherforecast` endpoint, and trading-ui is the default Vite + React page. `deploy/`, `tests/` and `docs/adr/` exist but are empty. The repo is not under git yet.

## Layout

- `src/Services/OrderGateway/`: ASP.NET Core minimal API (.NET 10, nullable enabled). Everything lives in `Program.cs`. OpenAPI is mapped only in Development. Dev URLs are `http://localhost:5082` and `https://localhost:7035` (from `Properties/launchSettings.json`).
- `src/web/trading-ui/`: React 19 + TypeScript + Vite 8 SPA, linted with ESLint flat config.
- `docs/adr/`: meant for architecture decision records.

There is no solution file, and the UI is not wired to the gateway yet (no Vite proxy or API client).

## Commands

OrderGateway (from `src/Services/OrderGateway`):
- `dotnet run` (add `--launch-profile https` for HTTPS)
- `dotnet build`
- `OrderGateway.http` holds sample requests.

trading-ui (from `src/web/trading-ui`):
- `npm run dev`: dev server with HMR
- `npm run build`: `tsc -b` type-check, then `vite build`
- `npm run lint`

No test projects or test runner are set up yet.
