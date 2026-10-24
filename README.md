# apify pricing: Every Plan and Real Cost Explained, Plus When a Flat-Rate Scraping API Like ScraperAPI Is the Better Fit

Apify pricing, in short: a free plan with $5 of monthly platform usage, Starter at $19/month, Scale at $199/month, Business at $999/month, and custom Enterprise pricing. Each paid plan includes platform usage equal to its price, with anything beyond that billed as you go. Independent pricing roundups checked in September 2026 also note annual billing takes about 10% off.

That's the sticker version. The version that matters for your budget is different, because Apify bills on consumption: compute units, proxy traffic, data transfer, and storage all come out of (or on top of) that prepaid allowance. Two users on the same $199 plan can end up with very different real costs depending on what they scrape and which Actors they run. And if your actual job is simpler — send a URL, get clean HTML or JSON back — a per-request API like ScraperAPI prices that work very differently, often at a lower entry point.

This piece walks through both: Apify's full plan table and the billing mechanics most summaries skip, then ScraperAPI's plans, credit math, and refund terms, so you can match the pricing model to your workload instead of guessing.

> **Quick pick:** If your task is "fetch pages from these URLs and give me the data," ScraperAPI's Hobby plan at $49/month ($44.10 billed annually, 100,000 credits, 20 concurrent threads) covers it, and there's a 7-day no-questions-asked refund behind it. 👉 [Check ScraperAPI's current plans and pricing](https://www.scraperapi.com/pricing?fp_ref=coupons)
>
> Apify fits better when you need to run full Actors — scheduled crawls, proxy rotation built in, datasets, and an entire store of ready-made scrapers. More on that below.

## Apify pricing at a glance

Apify currently publishes four self-serve plans plus a custom Enterprise tier. Here's the official pricing page, condensed:

| Plan | Monthly price | Included usage | CU rate | Actor RAM | Max concurrent runs |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | $5/month | $0.20/CU | 16 GB | 5 |
| Starter | $19 | $19/month + pay as you go | $0.20/CU | 64 GB | 32 |
| Scale | $199 | $199/month + pay as you go | $0.16/CU | 256 GB | 128 |
| Business | $999 | $999/month + pay as you go | $0.13/CU | 512 GB | 256 |
| Enterprise | Custom | Custom | Custom | Custom | Custom |

A CU (compute unit) is defined as 1 GB of RAM running for one hour. Support scales from Community on Free, to Chat on Starter, Priority chat on Scale, and a dedicated account manager on Business. Starter, Scale, and Business also get Bronze, Silver, and Gold discounts in Apify Store respectively.

## How Apify's credit system actually bills you

Every paid plan includes prepaid usage equal to its monthly price, and Apify is explicit about what happens to credits you don't spend: "unused usage credits are not rolled over to the next billing cycle, and they expire at the end of the billing cycle." Money left on the table each month is gone.

On the free tier the stakes are higher. If you blow through your $5 before the month ends, Apify shuts service off until the next billing cycle starts. There's no overage billing on Free — just a hard stop. For paid plans, overage is charged to your next bill and you get notified.

Actor pricing in Apify Store runs on two models, and it's worth knowing which one your target Actor uses:

1. **Pay per event** — the developer sets fixed prices for defined events (starting the Actor, returning a result). Most Actors bake platform usage into the event price, but some charge separately, so check the pricing section on the Actor's page.
2. **Pay per usage** — the developer adds no markup and you pay raw platform consumption: compute units, data transfer, storage operations, and any proxies the run uses.

Both models draw down your prepaid plan credits. Even reading from a dataset after a run finishes counts as platform usage.

There are also add-ons if you outgrow your plan's limits: extra concurrent runs cost $5 per run, extra Actor RAM is $1 per GB, and one-on-one technical training on Starter runs $150 per hour.

## The costs most pricing summaries bury: proxies, transfer, storage

The plan table gets all the attention, but for many workloads the per-unit resource prices matter more. These are the official rates:

- **Residential proxies:** $8/GB on Free and Starter, $7.50 on Scale, $7 on Business.
- **Datacenter proxies:** 5 IPs included on Free, 30 on Starter (then $1/IP), 200 on Scale (then $0.80/IP), 500 on Business (then $0.60/IP).
- **Google SERP proxies:** $2.50 per 1,000 SERPs on lower tiers, $2 on Scale, $1.70 on Business.
- **Unblocker:** $1.50 per 1,000 requests, dropping to $1.25 and $1 on the upper tiers.
- **External data transfer:** $0.20/GB on Free through Scale, $0.18 on Business.

Storage is metered too. Dataset timed storage runs $1.00 per 1,000 GB-hours ($0.80 on Business), request queue storage is $4.00 per 1,000 GB-hours, and reads/writes are billed in fractions of a cent per thousand operations. None of these numbers is large individually. Together, on a job that runs daily and stores results, they're the difference between "$19/month" and "$19 plus another $15 in metered usage."

A scraping job that pulls 1 GB of page data costs $0.20 in external transfer alone on the lower tiers — worth keeping in mind if your Actor exports large datasets.

## Which Apify tier fits which workload

The cheapest tier that clears your resource ceiling is the right one. Concretely:

- **Free ($0):** testing Actors, small one-off jobs. $5 of usage goes roughly one to two hours of a single-CU run plus light storage, so treat it as evaluation, not production.
- **Starter ($19):** a personal project running one or two Actors on a schedule, under 32 concurrent runs, no heavy proxy usage.
- **Scale ($199):** production crawls needing 128 concurrent runs, 256 GB RAM, or meaningful residential proxy volume — the $0.50/GB discount on residential proxies pays for itself quickly at scale.
- **Business ($999):** teams running many Actors in parallel, needing 256 concurrency and an account manager.

Apify's own advice, which is sound: run one test of your target Actor, then check the Billing page to see what it actually consumed before committing to a tier. Estimated costs and real costs on this platform diverge more than most.

## The flat-rate alternative: ScraperAPI pricing

If what you want is page data rather than a scraping platform, ScraperAPI bills per request instead of per compute-hour. You send a URL with parameters, it handles proxies, browser rendering, CAPTCHAs, and retries, and returns HTML or parsed JSON. Here's its full published plan set:

| Plan | Monthly | Annual (per month) | API credits/month | Concurrent threads | Link |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [ Get Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [ Get Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [ Get Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [ Get Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [ Get Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [ Get Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | [ Talk to sales](https://www.scraperapi.com/?fp_ref=coupons) |

Every paid plan includes JS rendering, premium residential and mobile IPs, advanced anti-bot bypassing, structured data parsing APIs, DataPipeline, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Geotargeting is the main gating feature: Hobby and Startup are limited to US and EU locations, while country-level targeting worldwide requires Business ($299) or above. Analytics history is capped at the last 30 days on the two cheaper plans and unlimited from Business up.

Overage handling is forgiving in one direction: if you exceed your plan's concurrency limit, ScraperAPI returns a 429 asking you to throttle — "There's no extra charge for going over, the request is simply turned away rather than queued." When credits run out, scraping pauses by default. On Hobby through Professional you can opt into auto-upgrade, which bumps you to the next tier (usually at a better per-credit rate) automatically. Pay-as-you-go, where you keep scraping at a fixed per-credit rate up to a monthly spending cap you set, is only available from Scaling up — a detail worth knowing before you pick a plan if your volume spikes unpredictably.

👉 [Compare all ScraperAPI plans on the pricing page](https://www.scraperapi.com/pricing?fp_ref=coupons)

## The credit math most reviews skip

Here's the part that changes real cost calculations, and that most Apify-versus-alternatives roundups never spell out: on ScraperAPI, one credit equals a *standard* page, but many high-value targets cost far more.

The official multipliers:

| Target type | Credits per request |
| --- | --- |
| Normal pages | 1 |
| E-commerce (Amazon, Walmart, eBay) | 5 |
| SERPs (Google, Bing, incl. subdomains) | 25 |
| LinkedIn | 30 |
| Anti-bot bypass (Cloudflare, Datadome, PerimeterX, Akamai) | +10 |

Parameters stack on top: `premium=true` adds 10 credits, `render=true` adds 10, both together 25. `ultra_premium=true` adds 30 and is only available on paid plans; combined with rendering it's 75. The good news: `country_code`, `session_number`, `device_type`, `autoparse`, and several others carry no surcharge.

Run the numbers on the Hobby plan's 100,000 monthly credits:

- Plain pages: 100,000 requests
- Amazon product pages: 20,000 requests
- Google SERPs: 4,000 requests
- LinkedIn profiles: about 3,300 requests

Same plan, a 30x spread in actual output depending on target. That's why the billing rules matter: ScraperAPI only charges for successful requests (HTTP 200 and 404), plus requests you cancel yourself before 70 seconds. Failed fetches behind a blocked target don't drain your balance — a meaningful difference from metered platforms where a hung run keeps burning compute.

Two practical tools keep this under control. The `sa-credit-cost` response header on every request shows exactly what it consumed, the dashboard's Domain Cost Estimator prices any URL before you scrape it, and you can set a `max_cost` parameter to hard-cap any single request. There's also a cost-check API endpoint (`api.scraperapi.com/account/urlcost`) if you'd rather script it.

## Free tiers, side by side

Both services give you something to test with before paying:

- **Apify Free:** $5 of platform usage monthly, 5 concurrent runs, 16 GB Actor RAM, no credit card. Enough to run small Actors a few times and inspect the billing pattern.
- **ScraperAPI Free:** 1,000 API credits per month at up to 5 concurrent connections, plus a 5,000-credit 7-day trial after signup with no card required. Ultra-premium proxies are excluded from the free tier.

One structural difference: ScraperAPI's free tier is request-based, so you always know what a test costs (1 credit × domain multiplier). Apify's free tier is consumption-based, so the same $5 stretches differently depending on which Actor and proxies a run touches.

## Refunds, cancellation, and billing safety

ScraperAPI offers a 7-day no-questions-asked refund on paid plans — contact support and they process it. You can cancel any time from the dashboard, and per the official docs, "You will not be charged for cancelling." Card details can be swapped from the Billing page whenever needed.

If you want to verify the service against your actual targets before any commitment, the signup path gives you 5,000 free trial requests for 7 days without a card. 👉 [Start the free ScraperAPI trial](https://www.scraperapi.com/?fp_ref=coupons)

The Pay-As-You-Go spending cap deserves a mention here too, since it's a billing-safety feature: you set a monthly limit, and the service won't exceed it unless you change the setting yourself. It's a cap, not a pre-charge.

## FAQ

**How much does Apify cost per month?**
$0 for the Free plan with $5 of usage, $19 for Starter, $199 for Scale, $999 for Business, and custom pricing for Enterprise. Paid plans include usage equal to their price; unused credits expire at each billing cycle.

**What is a compute unit on Apify?**
One GB of RAM running for one hour. Rates run $0.20/CU on Free and Starter, $0.16 on Scale, and $0.13 on Business. A run that holds 2 GB of RAM for three hours consumes 6 CUs.

**Is Apify or ScraperAPI cheaper?**
It depends entirely on workload shape. For fetching standard pages at modest volume, ScraperAPI's $49 Hobby plan undercuts everything on Apify's paid ladder. For scraping Google or Amazon heavily, ScraperAPI's credit multipliers (25 and 5 respectively) push the effective cost up, and Apify's Scale plan with built-in SERP proxies at $2/1,000 SERPs can be competitive. For complex, scheduled, multi-step crawls that need Actors, storage, and scheduling in one place, Apify has no flat-rate equivalent at all.

**Does Apify offer an annual discount?**
Multiple independent pricing roundups verified in September 2026 report annual billing takes 10% off. Confirm the exact figure on Apify's billing page at checkout, since promotions change.

**What happens if I go over my ScraperAPI limit?**
On concurrency, you get a 429 response and no charge. On credits, scraping pauses until renewal unless you've enabled auto-upgrade or, on Scaling and above, pay-as-you-go with a spending cap.

## Picking between them, concretely

Your target sites are mostly standard pages and your volume is under ~100,000 fetches a month → ScraperAPI Hobby at $49, annual $44.10, with the 7-day refund as your exit ramp. You're scraping Google or LinkedIn at volume → either budget for the multiplier (ScraperAPI Scaling and up, with pay-as-you-go smoothing spikes) or compare against Apify's Scale plan before committing. You need scheduled multi-step crawls with datasets and ready-made Actors → Apify's Starter or Scale is the tool built for that, and no request-based API replaces it.

One last check before you buy either way: run a single test request against your hardest target URL and multiply out the real per-request or per-run cost. The sticker price on both platforms is the least informative number on the page. 👉 [See ScraperAPI's plans and start risk-free](https://www.scraperapi.com/pricing?fp_ref=coupons)
