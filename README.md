# AI Credit Economics Simulator

A single-page interactive model of how a website builder prices AI features through plan credits. Set the plan tiers, the provider rate card, the task prices, and the usage distribution, then read what happens to margin, breakage, and revenue under different pricing policies.

**Live page:** https://evoln47.github.io/ai-credit-economics-simulator/

## What it does

- **Tier margin table** — for each plan, the included credits, the expected AI serving cost at median, p90, and p99 usage, the gross margin, and a guardrail flag where margin falls below a floor you set.
- **Allowance picker** — place the included credits at a chosen percentile of simulated usage and read breakage and margin at that allowance.
- **Policy toggles** — rollover on or off, and shortfalls handled as a hard cap, overage billing, or prepaid top-ups. Every toggle reprices revenue, margin, and breakage live.
- **Margin decomposition** — change a provider price, the model routing mix, or usage growth, and the margin change is split into rate, mix, volume, and interaction effects.
- **Benchmarks** — published credit mechanics from Framer, Wix, and Webflow next to the modeled tiers.
- **Decisions memo** — a plain-language record of the current settings and the reasoning they imply, generated from the model state.

## Defaults and sources

Everything on the page is editable, and every figure carries its assumption next to it.

- Plan tiers default to Squarespace's published plans (Basic $19/mo with 10 one-time AI credits, Core $29/mo with 20 credits/month, Plus $49/mo with 40/month, Advanced $99/mo with 120/month), from squarespace.com/pricing, checked October 2026.
- The provider rate card defaults to public per-token list prices as of November 2026 and is date-stamped on the page.
- Usage defaults to a lognormal distribution (median 20, p90 200, p99 1,500 actions per user per month). The model runs a seeded Monte Carlo of 10,000 users per tier over six months and reports the steady-state month.
- The top-up policy assumes half of any shortfall is covered by top-up purchases and the rest is forgone. That assumption is printed on the page where it applies.

## Running it

Open the live page above, or open `index.html` in any browser. There is no build step and no server; all computation runs locally on the page.

## Note

A personal modeling project built from public pricing pages and published competitor documentation. It is not affiliated with Squarespace or any provider named in the defaults.
