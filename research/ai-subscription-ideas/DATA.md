# Trends data notes

Pull date: 2026-10-28. Tool: pytrends 4.9.2 (`TrendReq`, hl `en-US` or noted, tz 360). Timeframe: `today 5-y` weekly. Partial weeks dropped. Geo `US` unless noted.

Scores are relative inside one request. 100 = peak week of the hottest term in that request. Do not compare a raw mean from one table to a raw mean from another. Ratios in the report are computed inside a single table.

Google samples Trends. A repeat pull will move these integers slightly. Rising-query values are Google's percent-growth figures versus a prior window; year-stamped queries inflate them. Use them to see brands, homework, and off-topic pollution, not as a count of searches.

One batch (`home_phrases`) hit HTTP 429 on the first pass and was collected later the same day. Figures below are from completed responses only.

## Canonical finalist chart (US)

One request. Keywords: `estimated taxes`, `llc tax`, `texas franchise tax`, `irmaa`, `quarterly taxes`. Weeks from 2021-10-24 through 2026-10-18 (n=261).

| keyword | 5y mean | 5y median | 5y max | last 52w mean | prior 52w mean | yoy | peak month each year |
|---|---:|---:|---:|---:|---:|---:|---|
| llc tax | 32.04 | 27 | 100 | 46.71 | 33.46 | 1.40 | Feb or Mar |
| estimated taxes | 10.85 | 8 | 49 | 13.87 | 12.13 | 1.14 | Apr every year 2022–2026 |
| irmaa | 8.33 | 6 | 29 | 17.54 | 9.44 | 1.86 | Nov/Dec; 2026 so far Oct |
| quarterly taxes | 6.85 | 6 | 25 | 8.08 | 7.33 | 1.10 | Apr every year |
| texas franchise tax | 3.63 | 3 | 14 | 4.31 | 3.50 | 1.23 | May every year |

Month means (index points on this chart):

| month | estimated taxes | quarterly taxes | llc tax | texas franchise tax | irmaa |
|---:|---:|---:|---:|---:|---:|
| 1 | 15.5 | 8.7 | 36.8 | 3.1 | 7.9 |
| 2 | 10.2 | 6.0 | 44.3 | 4.2 | 8.0 |
| 3 | 14.6 | 9.0 | 48.7 | 4.8 | 8.7 |
| 4 | 22.2 | 12.6 | 43.1 | 5.2 | 7.2 |
| 5 | 7.8 | 5.7 | 29.9 | 6.8 | 7.4 |
| 6 | 13.5 | 9.0 | 31.5 | 2.6 | 6.5 |
| 7 | 6.0 | 5.6 | 28.0 | 2.8 | 6.5 |
| 8 | 7.1 | 5.5 | 25.5 | 3.5 | 8.2 |
| 9 | 12.4 | 7.7 | 25.2 | 3.2 | 7.6 |
| 10 | 6.3 | 4.3 | 23.6 | 2.8 | 9.7 |
| 11 | 5.5 | 3.3 | 22.5 | 2.6 | 11.4 |
| 12 | 9.4 | 4.9 | 25.7 | 2.0 | 10.7 |

IRS estimated-tax dates (Q4 1/15, Q1 4/15, Q2 6/15, Q3 9/15) line up with the estimated-tax row. Texas franchise filing date (5/15) lines up with that row. IRMAA lines up with fall open enrollment and the bracket-release window.

## Mass ladder (US, separate request)

Do not mix these means with the finalist chart.

| keyword | 5y mean | max | last 52w | prior 52w | yoy | peak month |
|---|---:|---:|---:|---:|---:|---|
| medicare | 42.22 | 86 | 54.42 | 45.58 | 1.19 | Oct, then Nov |
| car insurance | 33.32 | 90 | 60.54 | 34.02 | 1.78 | Jul, then Aug |
| property tax | 20.49 | 41 | 25.77 | 22.21 | 1.16 | Mar, then Apr |
| fafsa | 19.71 | 97 | 18.44 | 21.60 | 0.85 | Jan, then Dec |
| turbotax | 19.28 | 100 | 16.54 | 17.48 | 0.95 | Feb, then Apr |

A different request that also contained `car insurance` (mean 33.74) and `medicare` (42.87) put `homeowners insurance` at 4.56 and `estimated taxes` at 0.72. Those two mass-market anchors match the table above within about 2%, so homeowners insurance sits near 4.6 and estimated taxes near 0.7 on this ladder. Estimated taxes is real and far below TurboTax; it is not a floor term.

`tax refund` on a TurboTax-anchored chart peaks every February (means: TurboTax 19.5, tax refund 11.8, estimated taxes 0.72 when TurboTax's peak week is 100). Seasonality of the refund query is the sanity check that the client was returning real Trends data.

## Mid-tier chart that contains homeowners insurance (US)

| keyword | 5y mean | max | last 52w | prior 52w | yoy | vs estimated taxes |
|---|---:|---:|---:|---:|---:|---:|
| homeowners insurance | 33.41 | 100 | 64.15 | 32.75 | 1.96 | 6.05x |
| franchise tax | 10.49 | 29 | 12.58 | 10.37 | 1.21 | 1.90x |
| obamacare | 8.63 | 48 | 9.64 | 8.98 | 1.07 | 1.56x |
| estimated taxes | 5.52 | 25 | 7.12 | 6.15 | 1.16 | 1 |
| backdoor roth | 5.05 | 16 | 6.89 | 5.79 | 1.19 | 0.92x |

`franchise tax` at 1.90x is not clean demand. See related queries. Homeowners at 6x is real level and a real doubling, and the related queries are quote/carrier intent plus off-topic rising terms.

## Job-tier chart where estimated taxes peaks at 100 (US)

Several requests returned `estimated taxes` with mean 22.08–22.09 and max 100. Terms below are from those requests and share that scale. Ratio = term mean / 22.08.

| keyword | mean | max | pct weeks at 0 | last 52w | prior 52w | ratio to estimated taxes | peak |
|---|---:|---:|---:|---:|---:|---:|---|
| estimated taxes | 22.08 | 100 | 0 | 28.12 | 24.81 | 1 | Apr |
| backdoor roth | 20.13 | 63 | 0 | 27.33 | 23.25 | 0.91 | Mar / Dec |
| roth conversion | 19.79 | 60 | 0 | 34.77 | 22.75 | 0.90 | Mar / Dec |
| irmaa | 17.01 | 59 | 0 | 35.67 | 19.48 | 0.77 | Nov / Dec |
| beneficial ownership | 11.30 | 88 | 0 | 13.60 | 19.85 | 0.51 | Dec historically; fading |
| premium tax credit | 8.41 | 32 | 0 | 15.00 | 8.69 | 0.38 | Mar–Apr and Nov–Dec |
| gambling winnings | 6.46 | 23 | 0 | 9.92 | 6.62 | 0.29 | Feb / Mar |
| tax loss harvesting | 4.38 | 22 | 0 | 6.56 | 4.27 | 0.20 | Dec |
| property tax appeal | 4.07 | 17 | 0 | 6.33 | 4.64 | 0.18 | May |
| rsu tax | 3.22 | 11 | 0 | 3.85 | 3.44 | 0.15 | Mar |
| healthsherpa | 3.26 | 10 | 0 | 3.58 | 3.85 | 0.15 | Nov / Dec |
| alternative minimum tax | 2.64 | 8 | 0 | 3.37 | 2.71 | 0.12 | Apr |
| ownwell | 2.45 | 27 | 30 | 5.02 | 3.81 | 0.11 | Apr / May |
| sales tax nexus | 2.03 | 5 | 0.4 | 3.10 | 2.00 | 0.09 | flat |
| keeper tax | 1.33 | 6 | 14 | 2.00 | 1.17 | 0.06 | Feb / Apr |
| economic nexus | 1.35 | 5 | 5 | 2.64 | 1.25 | 0.06 | flat |
| form 5472 | 1.27 | 8 | 12 | 2.56 | 0.94 | 0.06 | weak |
| incentive stock options | 1.08 | 6 | 15 | 1.83 | 0.90 | 0.05 | Apr |
| insurance nonrenewal | 0.16 | 2 | 85 | 0.67 | 0.08 | 0.007 | none |
| hoa nonrenewal | 0 | 0 | 100 | 0 | 0 | 0 | none |
| flyfin | 0.04 | 1 | 96 | 0 | 0.04 | ~0 | none |

On this 22.08 scale, IRMAA's last-52-week mean (35.7) exceeds estimated taxes (28.1). The finalist chart shows the same crossover (17.5 vs 13.9).

### Tax-family sibling chart (US)

`estimated taxes` is the peak on this request too, but its mean is 20.04 (max 100), not 22.08. Ratios below use 20.04. Do not place these means on the 22.08 scale.

| keyword | mean | max | ratio to estimated taxes | peak |
|---|---:|---:|---:|---|
| estimated taxes | 20.04 | 100 | 1 | Apr every year |
| self employment tax | 14.25 | 43 | 0.71 | Apr |
| quarterly taxes | 12.71 | 46 | 0.63 | Apr every year |
| underpayment penalty | 5.04 | 30 | 0.25 | Apr every year |
| quarterly estimated taxes | 2.10 | 11 | 0.10 | Apr every year |

`quarterly taxes` at 0.63x matches the finalist chart (6.85 / 10.85 = 0.63).

## ACA wording (US, one request)

| keyword | mean | ratio to estimated taxes | last 52w | prior 52w | yoy | peak |
|---|---:|---:|---:|---:|---:|---|
| obamacare | 18.02 | 1.55 | 20.17 | 18.69 | 1.08 | Nov |
| health insurance marketplace | 16.31 | 1.40 | 23.90 | 19.04 | 1.26 | Nov / Jan |
| estimated taxes | 11.62 | 1 | 14.79 | 13.02 | 1.14 | Apr |
| premium tax credit | 4.45 | 0.38 | 7.90 | 4.62 | 1.71 | Jan–Apr |
| aca marketplace | 2.18 | 0.19 | 6.14 | 1.94 | 3.16 | Nov, from a small base |

The 0.38 ratio for premium tax credit matches the job-tier chart.

## Insurance phrases (US, one request)

`homeowners insurance` mean 33.41, max 100, same series as the mid-tier chart.

| keyword | mean | share of homeowners insurance |
|---|---:|---:|
| homeowners insurance | 33.41 | 1 |
| flood insurance | 8.06 | 0.24 |
| insurance escrow | 1.51 | 0.045 |
| california fair plan | 1.31 | 0.039 |
| home insurance increase | 0.91 | 0.027 |

## Student-aid chart (US)

| keyword | mean | max | last 52w | prior 52w | pct weeks at 0 | peak |
|---|---:|---:|---:|---:|---:|---|
| fafsa | 19.45 | 96 | 18.23 | 21.25 | 0 | Jan |
| student loans | 9.48 | 100 | 8.50 | 8.62 | 0 | uneven; a spike set the max |
| student loan forgiveness | 4.81 | 99 | 1.12 | 1.42 | 0 | spike, then collapse |
| save plan | 0.82 | 5 | 1.21 | 1.04 | 34 | Aug, then Sep |
| income driven repayment | 0 | 0 | 0 | 0 | 100 | none |

## Gig / spike chart (US)

Ratios are valid inside the request. Means of the spike terms are not "levels" because most weeks are zero and one week sets 100.

| keyword | mean | max | pct weeks at 0 | ratio to estimated taxes | yoy |
|---|---:|---:|---:|---:|---:|
| estimated taxes | 5.69 | 26 | 0 | 1 | 1.15 |
| crypto tax | 4.15 | 14 | 0 | 0.73 | 1.63 |
| no tax on overtime | 3.96 | 100 | 58 | n/a as a level | 0.42 |
| no tax on tips | 2.02 | 63 | 56 | n/a as a level | 0.55 |
| doordash taxes | 1.70 | 7 | 0 | 0.30 | 1.26 |

`doordash taxes` peaks in January every year 2022–2026.

## State franchise wording (US)

| keyword | mean | max | peak |
|---|---:|---:|---|
| llc tax | 32.04 | 100 | Mar |
| franchise tax | 20.44 | 57 | Apr |
| california franchise tax | 4.66 | 18 | Apr |
| texas franchise tax | 3.63 | 14 | May |
| delaware franchise tax | 1.10 | 7 | Feb |

`llc tax` / `franchise tax` = 1.57 inside this request. The finalist chart is the one that places `llc tax` against `estimated taxes` directly (2.95x). Do not multiply these ratios again.

## Regions (US, 5y, interest by region, low volume included)

`franchise tax`: California 100, Texas 49, Wyoming 28, Arkansas 26, Delaware 26, District of Columbia 21, Nevada 19, Tennessee 19. This index is relative interest, so small formation states rank high per capita. It is not a volume ranking. Combined with related queries, California is inflated by Franchise Tax Board navigational search.

`property tax protest`: Texas 100, Nebraska 15, Wyoming 15, Colorado 14. Effectively a Texas query.

## Great Britain (5y)

Self-assessment batch:

| keyword | mean | max | pct weeks at 0 | peak |
|---|---:|---:|---:|---|
| companies house | 77.22 | 100 | 0 | flat; Feb 85, Dec 66 |
| self assessment | 16.00 | 86 | 0 | January |
| tax return | 11.25 | 49 | 0 | January |
| confirmation statement | 1.19 | 2 | 0.4 | flat |
| payments on account | 0.30 | 2 | 70 | none usable |

Scale batch, same country, different 100: mortgage 42.5, council tax 30.0, student finance 10.3, self assessment 7.2, home insurance 6.5. Self Assessment is a real January spike and smaller than council tax. Companies House dwarfs it and does not spike on a filing deadline.

## China (geo CN, hl zh-CN, 5y)

Not a measure of Baidu / WeChat demand. Reported only so the empty result is on the record.

| keyword | mean | max | pct weeks at 0 | note |
|---|---:|---:|---:|---|
| 医保 | 11.93 | 100 | 0 | Nov peak, yoy 1.85, among Google users |
| 房贷 | 3.88 | 17 | 4 | Sep peak |
| 个人所得税 | 3.71 | 14 | 3 | Mar and Dec bumps |
| 车险 | 0.83 | 8 | 57 | thin |
| 个税汇算 | 0.01 | 2 | 99.6 | unusable |

## Related queries (5y, top of list)

Values in parentheses are Google's score for that list. Rising percents are growth versus a prior window.

### estimated taxes (US)

Top: pay estimated taxes (100), estimated taxes due (40), irs estimated taxes (39), pay estimated taxes online (33), federal estimated taxes (33), estimated tax payments (27), how to pay estimated taxes (25).

Rising is year-stamped due dates, including when are estimated taxes due 2026, plus pay federal estimated taxes online. No brand.

### quarterly taxes (US)

Top: pay quarterly taxes (100), quarterly taxes due (43), estimated quarterly taxes (39), how to pay quarterly taxes (35), file quarterly taxes (30), irs quarterly taxes (29).

Not sales-tax nexus language. One rising query is a gig-work homework prompt; the head of the list is not.

### irmaa (US)

Top: irmaa brackets (100), irmaa medicare (68), 2026 irmaa (60), irmaa 2025 (54), 2026 irmaa brackets (39), what is irmaa (29).

Rising: irmaa brackets by year, medicare irmaa 2026, irmaa brackets 2027. No consumer brand.

### premium tax credit (US)

Top: the premium tax credit (100), what is premium tax credit (68), what is the premium tax credit (42), premium tax credit 2026 (39), premium tax credit form (39), advance premium tax credit (35).

`premium tax credit 2026` is in the top list, not only the rising list. "What is" is a large share.

### llc tax (US)

Top: llc taxes (100), llc tax form (89), llc tax return (71), california llc tax (64), llc tax rate (59), llc tax filing (59).

Rising: filing deadlines by year (2022 through 2025 on the list returned).

### texas franchise tax (US)

Top: texas franchise tax instructions (100), form (94), threshold (76), search (75), return (70).

Rising includes threshold by year, instructions by year, and texas franchise tax no tax due report.

### franchise tax (US) — polluted head term

Top: california franchise tax (100), franchise tax board california (77), franchise tax texas (72), ca franchise tax (30), what is franchise tax (30), state franchise tax board (29).

The agency name Franchise Tax Board sits next to the tax. Texas filing queries are the clean slice and are smaller (see finalist chart).

### homeowners insurance (US) — level is real, rising list is not

Top: home insurance (100), best homeowners insurance (71), allstate insurance (58), car insurance (56), allstate (56), homeowners insurance quote (56).

Rising, off topic, in the order returned: comcast wifi, xfinity comcast, xfinity near me, toyota rav4, xfinity cable deals, toyota sienna price, toyota 4runner, toyota. Allstate quote appears only after those.

### flood insurance (US)

Top: what is flood insurance (100), cost (94), fema (88), fema flood insurance (86), florida flood insurance (83).

Rising includes the homework item beginning "why did maggie not have flood insurance" and a second "what should maggie do? check all that apply", plus "write a paragraph about the costs and benefits of having insurance."

### property tax protest (US)

Top: texas property tax protest (100), protest property taxes (58), property tax protest companies (34), deadline (34), Harris / Dallas / Travis county variants.

Rising, first entries: ownwell; ownwell property tax protest; ownwell property tax protest reviews; ownwell property tax reviews. Then Texas deadlines.

### ownwell (US)

Top and rising are reviews, property tax protest, login, reddit, Austin. Brand search tracks the April–May protest season.

### obamacare (US)

Top: obamacare insurance (100), health insurance (54), what is obamacare (52), obamacare enrollment (25), obamacare cost (23).

Rising mixes income limits and open enrollment with political queries (rebate checks, subsidy expiration headlines).

### fafsa (US)

Top: fafsa login (100), my fafsa (28), fafsa deadline (27), what is fafsa (27), fafsa application (23).

Rising is year stamps plus `sai fafsa`.

### backdoor roth (US)

Top: roth ira / ira (100), backdoor roth ira (96), mega roth backdoor (42), how to backdoor roth (30).

Rising is contribution limits by year, including 2026, and mega backdoor limits. The head term mixes backdoor and mega backdoor.

### form 5472 (US)

Top: 5472 instructions (100), form 1120 (54), form 5471 (30), pro forma 1120 (23), pdf (20). Real filing intent, small level.

### save plan (US)

Top: the save plan (100), what is the save plan (53), student loan save plan (38), save plan calculator (12).

Rising: forbearance, PSLF, studentaid.gov, transition deadline. A wind-down query, and a small line next to FAFSA.

### beneficial ownership (US)

Top and rising are BOI report, FinCEN, file, 2024 due date. Historical filing panic. The domestic obligation was removed by FinCEN's final rule effective 2026-08-14.

### companies house (GB)

Top: companies house beta (100), search companies house (79), uk companies house (76), company house (72), companies house login (34), companies house number (22).

Rising: verify identity / personal code / identity verification.

### self assessment (GB)

Top: self assessment hmrc (100), hmrc (97), self assessment login (93), self assessment tax return (45).

Rising includes a late-filing fine headline and `adhd self assessment`.

### payments on account (GB)

Top, on a near-floor term: hmrc payments on account (100), payments on account self assessment (46), reduce payments on account (42), what are payments on account (38), vat payments on account (19). Intent of the few searches is right. Volume is not.

## Requests that were not used as evidence

- A term queried alone. It always peaks at 100. Avoided for ranking.
- `income driven repayment` at all zeros beside FAFSA. Treated as below the quantization floor of that chart, not as a precise zero in absolute searches. It is still far below `save plan`, which itself was visible on the same chart.
- China Google Trends, as a readout of mainland demand.
- Rising-query percentages as if they were search counts.
