# proxy pricing: how per-GB and per-IP billing really works, and what every 9Proxy plan costs

Search "proxy pricing" and you get a wall of numbers that refuse to line up. One provider quotes per gigabyte, another per IP, a third per thousand requests. Some per-GB rates quietly assume a 10 GB minimum; others expire your unused traffic in 30 days. Two providers can both print "$3 per GB" and cost you five times as much for the same scraping job.

So the useful question isn't "which provider is cheapest." It's "which billing model matches how your workload actually consumes." Get that wrong and you're either paying for bandwidth you never touch, or paying per IP for traffic that barely uses them.

This page walks through the models, the math that separates them, the discount levers that actually move your bill, and — as a worked example — the full current rate card from 9Proxy, a residential proxy provider whose pay-per-IP-with-unlimited-bandwidth model makes the tradeoffs easy to see.

## The four pricing models you'll run into

Nearly every proxy quote you'll read falls into one of these:

| Model | What you pay for | Suits | The trap |
| --- | --- | --- | --- |
| Per GB | Bandwidth consumed | High-rotation work with small payloads: SERP checks, ad verification, API polling | Expiry windows and minimum commits |
| Per IP | Access to a number of IPs, bandwidth usually unlimited | Long sessions, account work, heavy data transfer | IPs are time-limited once activated |
| Subscription | A monthly traffic allowance | Predictable, steady monthly volume | Unused traffic resets at month end |
| Per request / per 1,000 | Individual calls through an unblocker or SERP API | You're buying outcomes, not proxies | Costs balloon on image-heavy or JS-heavy targets |

Two structural facts matter more than any single price. First, most residential providers rent you bandwidth — they don't sell you IPs. That's why per-GB is the default unit. Second, per-GB rates on pricing pages are almost always entry-tier rates, and entry-tier rates are almost always the worst rate you'll ever pay.

## Why "from $0.68 per GB" is never the number you pay

That headline figure is the largest tier's rate. It's real, but it's the price at 10,000 GB, not at 10 GB. Review-tracked entry rates across mainstream residential providers cluster somewhere between roughly $3 and $8 per GB at the 10 GB mark — Bright Data sits around $8.40/GB there, Oxylabs around $8/GB, Decodo closer to $3.50/GB. The spread isn't just branding; pool size, success rate and targeting depth are what the premium buys.

Four things change the number between the page and the invoice:

**Volume tiering.** Going from a 5 GB pack to a 1,000 GB pack can cut the per-GB rate by 70–80%. This is by far the biggest lever you control.

**Validity windows.** A 180-day expiry is generous. A 30-day expiry on a 100 GB pack means you're effectively renting a deadline. Non-expiring traffic is worth a small premium because it turns sunk cost into inventory.

**Selection and targeting fees.** Some providers charge more for city-level targeting, ISP filtering or mobile exit nodes. Always check whether your targeting needs are inside the base rate.

**Balance vs subscription.** Balance-based accounts let you buy once and draw down over time. Subscriptions reset monthly, so a slow month with a subscription is money gone.

## Per-GB or per-IP? The decision rule

There's a clean way to think about it.

> If your requests are small and you need a different IP every few seconds, buy bandwidth. If your sessions are long and you need one IP to hold an identity across minutes or hours, buy IPs.

Concretely: per-GB pricing wins for scraper fleets hammering thousands of small product pages, ad-fraud checks and rank tracking. Per-IP pricing wins when each IP has to carry a lot of traffic — video, bulk file pulls, long authenticated sessions, multi-account setups where the IP is the identity, not a disposable exit node.

The reason this matters is that unlimited bandwidth per IP only has value if you can actually push traffic through that IP before it rotates out of the pool.

## The break-even math that decides your invoice

Here's the arithmetic most buyers skip.

Take a 100-IP package at $24. That's $0.24 per IP, with bandwidth included. If those 100 IPs move 10 GB total during their lifetime, your effective rate is $2.40/GB — better than the entry GB tier, worse than the mid tiers. Push 300 GB through the same 100 IPs and your effective rate lands at $0.08/GB, well under even the cheapest standard GB pack.

The break-even against 9Proxy's lowest standard GB rate ($0.68/GB, at 10,000 GB) works out to roughly 35 GB. Cross that band on a 100-IP package and your effective per-GB cost beats a 10,000 GB purchase — with a $24 buy-in instead of $6,800.

The catch is the IP lifespan. Residential IPs on this kind of model stay usable for a few hours up to about 24 hours of active time, and unlimited bandwidth only helps during that window. If your workload can't consume the traffic fast, per-GB is the honest choice.

## One provider's full rate card, so the tiering stops being abstract

[9Proxy](https://bit.ly/9-Proxy) is a residential proxy provider running 20M+ IPs across 90+ countries, with country, state, city, ZIP and ISP-level targeting over HTTP, HTTPS and SOCKS5. It sells three ways: by IP, by GB, and in bundles that mix both.

One pricing note worth knowing before you read the table: 9Proxy raised IP-based and bundle rates on 1 June 2026 and left GB-based rates untouched. If you land on an older cached page, per-IP numbers will look lower than what's below.

| Package | What you get | Price | Effective rate | Notes | Buy |
| --- | --- | --- | --- | --- | --- |
| 100 IPs | Residential IPs, unlimited bandwidth | $24 | $0.24 / IP | Unused IPs never expire | [Grab the 100-IP starter pack](https://bit.ly/9-Proxy) |
| 500 IPs | Residential IPs, unlimited bandwidth | $72 | $0.144 / IP | Solo-operator tier | [Check the 500-IP package](https://bit.ly/9-Proxy) |
| 1,000 IPs + 500 bonus | 1,500 IPs, unlimited bandwidth | $126 | $0.084 / IP | Bonus IPs included | [See the 1,500-IP deal](https://bit.ly/9-Proxy) |
| 2,500 IPs | Residential IPs, unlimited bandwidth | $210 | $0.084 / IP | Same rate as the tier below | [View the 2,500-IP package](https://bit.ly/9-Proxy) |
| 5,000 IPs | Residential IPs, unlimited bandwidth | $360 | $0.072 / IP | Agency-scale workloads | [Open the 5,000-IP package](https://bit.ly/9-Proxy) |
| 15,000 IPs | Residential IPs, unlimited bandwidth | $720 | $0.048 / IP | Regional teams | [Check the 15,000-IP rate](https://bit.ly/9-Proxy) |
| 25,000 IPs | Residential IPs, unlimited bandwidth | $863 | ~$0.035 / IP | Reseller territory | [See the 25,000-IP tier](https://bit.ly/9-Proxy) |
| 50,000 IPs | Residential IPs, unlimited bandwidth | $1,438 | $0.029 / IP | High-volume resellers | [View the 50,000-IP tier](https://bit.ly/9-Proxy) |
| 100,000 IPs | Business IP package, unlimited bandwidth | $2,300 | $0.023 / IP | Industrial scale | [Explore the 100,000-IP package](https://bit.ly/9-Proxy) |
| 200,000 IPs | Business IP package, unlimited bandwidth | $4,140 | $0.021 / IP | Enterprise pricing | [Open the 200,000-IP tier](https://bit.ly/9-Proxy) |
| 500,000 IPs | Business IP package, unlimited bandwidth | $8,625 | $0.018 / IP | Lowest per-IP rate offered | [See the 500,000-IP tier](https://bit.ly/9-Proxy) |
| 5 GB | Bandwidth, unlimited endpoints | $15 | $3.00 / GB | 180-day validity | [Get the 5 GB pack](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | 55 GB of bandwidth | $105 | $2.10 / GB | 180-day validity | [Check the 55 GB pack](https://bit.ly/9-Proxy) |
| 100 GB | Bandwidth, unlimited endpoints | $150 | $1.50 / GB | 180-day validity | [View the 100 GB pack](https://bit.ly/9-Proxy) |
| 200 GB | Bandwidth, unlimited endpoints | $200 | $1.00 / GB | 180-day validity | [Open the 200 GB pack](https://bit.ly/9-Proxy) |
| 1,000 GB | Bandwidth, unlimited endpoints | $800 | $0.80 / GB | 180-day validity | [See the 1,000 GB pack](https://bit.ly/9-Proxy) |
| 2,000 GB | Bandwidth, unlimited endpoints | $1,500 | $0.75 / GB | 180-day validity | [Check the 2,000 GB pack](https://bit.ly/9-Proxy) |
| 3,000 GB | Enterprise bandwidth | $2,160 | $0.72 / GB | Traffic never expires | [View the 3,000 GB enterprise pack](https://bit.ly/9-Proxy) |
| 6,000 GB | Enterprise bandwidth | $4,200 | $0.70 / GB | Traffic never expires | [Open the 6,000 GB pack](https://bit.ly/9-Proxy) |
| 10,000 GB | Enterprise bandwidth | $6,800 | $0.68 / GB | Traffic never expires | [See the 10,000 GB pack](https://bit.ly/9-Proxy) |
| Starter bundle | 100 IPs + 5 GB | $30 | Mixed | 180-day traffic validity | [Grab the Starter bundle](https://bit.ly/9-Proxy) |
| Middle bundle | 1,500 IPs + 50 GB | $180 | Mixed | 180-day traffic validity | [Check the 1,500-IP bundle](https://bit.ly/9-Proxy) |
| Pro bundle | 5,000 IPs + 500 GB | $720 | Mixed | List price $860, ~16% off at checkout | [Open the Pro bundle](https://bit.ly/9-Proxy) |

Two structural differences hide in that table. IP-based plans need the desktop app for local port forwarding, and authentication runs through it. GB-based plans run straight from the browser dashboard with username/password or IP whitelisting, so they work on a VPS or in a cloud script with no install. If you're automating from a server, that alone may settle the choice for you.

Third-party testing is reasonably consistent with the pricing tier. Geekflare's 2026 test run of 300 requests logged a 97.7% success rate, a 0.63-second average response time and a low hard-block rate, with the handful of CAPTCHAs coming from a single IP range that resolved on rotation. ProxyBrief's breakdown puts the honest downside plainly: residential IPs drop naturally, and the desktop app requirement adds a setup step.

## Discounts: separating the real ones from the decoration

Coupon aggregators advertise "up to 81% off" and "$0.015 per IP." Those figures describe the *gap between the smallest and largest tiers*, not a code you can type at checkout. The tiering in the table above is the discount.

What genuinely exists beyond list price:

- **Referral and invite codes.** 9Proxy's affiliate program pays up to 15% commission with crypto payouts and gives referred users a 5% discount. Signing up through an invite link is the simplest way to start below list.
- **Seasonal GB campaigns.** The April 2026 campaign issued a personal 9% cashback coupon (code format `X9_[number]`) after a first paid GB order, auto-applying to the next GB purchase, valid through 30 June 2026. It excluded IP-based plans and bundles and couldn't be stacked.
- **Holiday coupons.** A Lunar New Year promotion ran 8% off regular IP and GB packages from late January to late February 2026, plus themed large packs.
- **Partner codes.** Some anti-detect browser vendors publish their own 9Proxy promo codes, typically small single-digit discounts.

The pattern is worth internalising: seasonal promos at this provider target GB orders, arrive automatically in your dashboard under My Coupons, and rarely stack. If you need a code, it's already in your account.

## Costs that don't appear on any pricing page

Your real bill includes things no provider lists next to the per-GB rate:

- **Retries.** A failed request that still transferred headers and markup still burned bandwidth. On targets with aggressive bot detection, budget 15–30% overhead.
- **Expiry.** 180-day validity on GB plans is generous, but it isn't infinite. Enterprise GB tiers remove the deadline entirely — that's the upgrade you're actually buying there.
- **Adjacent tooling.** Anti-detect browsers, CAPTCHA solvers and cloud phones are separate vendors with separate invoices. Proxies are one line in a stack, not the whole cost.
- **Refund friction.** Geekflare's review notes that Trustpilot complaints centre on the refund policy rather than the network itself — buyers who picked a mismatched plan couldn't recover the spend. Test small before committing to a tier.
- **No self-serve trial.** 9Proxy doesn't publish an instant free trial on the site; limited trial access is arranged through their community presence and depends on availability. Budget $24 for the 100-IP pack as your cheapest real test.

## A five-minute way to size your own bill

Skip the calculators. Do this instead:

1. **Estimate monthly bandwidth.** Run your scraper for an hour against a representative target and measure bytes transferred. Multiply out. Median HTML pages are 100–300 KB; image-heavy targets are 2–5 MB.
2. **Estimate peak concurrent sessions.** That's your IP count, not your request count. One sticky session per account or browser profile.
3. **Divide bandwidth by IPs.** If the answer is under 1 GB per IP per session, you're a per-GB buyer. If it's above a few GB, run the break-even above.
4. **Check the expiry against your execution window.** If the project finishes in two months, a 180-day window is free insurance. If it's a standing operation, pay for the non-expiring tier.
5. **Then pick the tier, not the provider.** Moving from a 100 IP pack to a 1,500 IP pack drops the per-IP rate from $0.24 to $0.084. That single decision usually beats hunting for a coupon code.

## FAQ

**Is per-GB or per-IP cheaper?**
Whichever matches your consumption. For small, high-rotation requests, per-GB. For long sessions that push real volume through few IPs, per-IP with unlimited bandwidth is usually cheaper and more predictable, because the cost doesn't move when your traffic spikes.

**Do unused proxies expire?**
At 9Proxy, unused IPs on balance-based accounts don't expire, and unused GB sits for 180 days — indefinitely on Enterprise tiers. Once an IP is activated and forwarded, expect a few hours up to around 24 hours of useful life.

**How much does a residential proxy actually cost?**
Entry-tier residential bandwidth across mainstream providers runs roughly $3–$8 per GB at low volume and can fall below $1 per GB at terabyte scale. Entry per-IP rates run from about $0.25 down to under $0.02 at hundreds of thousands of IPs.

**Why is the advertised price so much lower than what I pay?**
Because the advertised price is the top volume tier, and residential pricing is superlinear — every step down in unit cost requires a step up in commitment. The only honest way to compare providers is to price your actual monthly bandwidth and IP count against each tier.

If you'd rather test the tiering theory than take it on faith, the smallest package is the cheapest way to find out where your workload lands.

👉 [Start with 9Proxy's entry packages and see the live rates](https://bit.ly/9-Proxy)
