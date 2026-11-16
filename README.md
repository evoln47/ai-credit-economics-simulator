# AI Credit Economics Simulator

A single-page interactive model of how a website builder prices AI features through plan credits. Set the plan tiers, the provider rate card, the task prices, and the usage distribution, then read what happens to margin, breakage, and revenue under different pricing policies.

**Live page:** https://evoln47.github.io/ai-credit-economics-simulator/

## What it does

- **Tier margin table** — for each plan, the included credits, the expected AI serving cost at median, p90, and p99 usage inside the plan's own tier band, the gross margin, and a guardrail flag where margin falls below a floor you set.
- **Allowance picker** — place the included credits at a chosen percentile of the plan's own simulated usage and read breakage and margin at that allowance.
- **Policy toggles** — rollover on or off, and shortfalls handled as a hard cap, overage billing, or prepaid top-ups. The shortfall and rollover toggles reprice revenue, margin, and breakage live.
- **Margin decomposition** — change a provider price, the model routing mix, or usage growth, and the profit change, in dollars per user, is split into rate, mix, volume, and interaction effects.
- **Benchmarks** — published credit mechanics from Framer, Wix, and Webflow next to the modeled tiers.
- **Decisions memo** — a plain-language record of the current settings and the reasoning they imply, generated from the model state.
- **Fully loaded view (§10)** — a cost stack on top of the AI-serving figures: payment processing per subscriber (2.9% + $0.30 per monthly charge) and a non-AI cost of revenue line calibrated so the stack totals Squarespace's fiscal 2023 cost-of-revenue share (20.5% of revenue; gross margin 79.5%) at the defaults, plus an operating view at the filed fiscal 2023 expense shares. A switch chooses whether the §04 headline margin and its guardrail check report the AI-serving basis or the fully loaded basis.

## Defaults and sources

Everything on the page is editable. Assumptions are printed beside the controls they drive, and the Methodology view tags how each behavior default was checked.

- Plan tiers default to Squarespace's published plans (Basic $19/mo with 10 one-time AI credits, Core $29/mo with 20 credits/month, Plus $49/mo with 40/month, Advanced $99/mo with 120/month), from October 2026 pricing compilations. The evidence review's direct check of the pricing page failed, so the ladder is index-grade; the page's Methodology §09 records this.
- The provider rate card defaults to public per-token list prices as of November 2026 and is date-stamped on the page.
- Usage defaults to a lognormal distribution (median 20, p90 200, p99 1,500 actions per user per month). The model runs a seeded Monte Carlo of 40,000 users sorted into the four tiers by demand level, 10,000 per tier, over six months, and reports month six, so each tier is read on its own band of the usage distribution.
- The top-up policy assumes half of any shortfall is covered by top-up purchases and the rest is forgone. That assumption is printed on the page where it applies. The behavior layer then restates top-up and overage revenue at the paid take-up rate (20% of wall users by default, an assumption with no published value); under the top-up policy each payer buys half of their shortfall.

## Running it

Open the live page above, or open `index.html` in any browser. There is no build step and no server; all computation runs locally on the page.

## Note

A personal modeling project built from public pricing pages and published competitor documentation. It is not affiliated with Squarespace or any provider named in the defaults.
