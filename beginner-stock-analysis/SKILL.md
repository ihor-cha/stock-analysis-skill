---
name: beginner-stock-analysis
description: Gives a simple, educational valuation snapshot of a listed stock when the user provides a company name, ticker or ISIN. Covers EV/EBITDA, P/E, P/B, EV/Sales and other basic ratios, compares the current multiple with the company's own history and with its peers, and explains every metric in plain language for inexperienced investors. Make sure to use this skill whenever the user mentions a stock, share, ticker or ISIN and wants to analyse it, check whether it looks cheap or expensive, compare it with competitors, understand a valuation ratio, or learn how to analyse stocks, even if they don't say "analysis" or name any ratio.
---

# Beginner Stock Analysis

Turn a stock name, ticker or ISIN into a short, clear valuation snapshot that also teaches the reader how to read it. The audience is an inexperienced investor. The goal is that they finish the answer understanding the company's valuation better *and* understanding the ratios better than before.

This is an educational tool, not investment advice. Never tell the user to buy, sell or hold, and never give price targets or forecasts. Describe what the numbers show and what they do not show.

## Workflow

### 1. Identify the company

Accept a company name, ticker or ISIN.

- An ISIN starts with a two-letter country code (e.g. DE, US, NL). Use search to resolve it to the company and its primary listing.
- Confirm company, exchange and trading currency in the output. Many companies have several listings and share classes, and mixing them gives wrong numbers.
- If the input could match more than one company, ask one short clarifying question before continuing. Do not guess.

### 2. Gather real data

Use web search, web fetch or any connected financial-data tool to retrieve current figures. Read `references/data-sources.md` for what to collect and where to look.

The most important rule: **every number must come from a source you actually retrieved, with its date.** If you cannot find a figure, write "not found" instead of filling it in from memory. Beginners cannot tell a made-up ratio from a real one, so a wrong number does more harm than a gap. If two sources disagree, show the range and say so.

Prefer the company's own reports and exchange or regulator filings for fundamentals, and reputable financial-data sites for prices and consensus-type data. Compute ratios yourself from the components when you can, so the method is consistent between the company and its peers.

### 3. Check which ratios make sense

Not every ratio fits every business. Before calculating, read the applicability table in `references/metrics-guide.md`. Key cases:

- Banks and insurers: skip EV/EBITDA (debt is their raw material). Use P/E, P/B and return on equity.
- Real estate companies and REITs: use P/FFO or price vs. net asset value in addition to P/E.
- Loss-making or negative-EBITDA companies: mark EV/EBITDA and P/E as "not meaningful" and use EV/Sales, explaining why.
- Cyclical companies (mining, chemicals, shipping, autos): warn that P/E and EV/EBITDA look cheapest at peak earnings and most expensive at the bottom of the cycle.

Telling the user *why* a ratio is skipped is part of the education, so do it in one sentence.

### 4. Compare with the company's own history

Show the current multiple next to its own 5-year (ideally 10-year) average and range, and say where it sits: near the low end, middle or high end of its own range. If a historical series is not available, estimate it from past year-end prices and reported figures, and label it clearly as an approximation. If neither is possible, say that history was not available.

Mention when something structural changed (large acquisition, change of business model, accounting change) because that makes old multiples less comparable.

### 5. Compare with peers

Pick 3 to 5 peers: same industry and business model, similar size, preferably the same region. Say in one line why these peers were chosen. Show each peer's multiples, the peer median, and where the company sits relative to the median.

A company trading above its peers is not automatically overpriced; faster growth, higher margins or lower risk can justify a premium. Always mention growth and margin differences when they explain the gap. For European companies, check that EBITDA is treated consistently for lease accounting across peers (see the metrics guide).

### 6. Write the answer in the standard format

Use this structure. Keep it compact; beginners read short answers, not long ones.

```
# [Company] ([Ticker] · [ISIN] · [Exchange], [Currency])
Data as of [date]. Sources: [list]

## Snapshot
| Metric | Value | What it tells you |
(EV/EBITDA, P/E, P/B, EV/Sales, FCF yield, dividend yield, net debt/EBITDA, plus anything else relevant. Last column: one plain-English sentence per metric.)

## Versus its own history
(Current vs. 5-year average and range, one or two sentences of interpretation.)

## Versus peers
| Company | EV/EBITDA | P/E | P/B | Growth | Margin |
(Include the peer median row. One or two sentences of interpretation.)

## How to read this
(3 to 5 sentences in plain language: what the numbers suggest about valuation relative to history and peers, and what could explain it. Balanced, no recommendation.)

## What these ratios do not tell you
(2 to 3 things a ratio cannot show: debt and risk, business quality, growth outlook, one-off effects. Make them specific to this company.)

## Learn: [one concept]
(A short explanation, 2 to 4 sentences with an everyday analogy, of the single most useful concept for understanding this particular analysis, e.g. why EV/EBITDA is used instead of P/E for indebted companies.)

*Educational overview only, not investment advice. Figures come from public sources and may contain errors or be out of date; check them against the company's own reports before making decisions.*
```

## Teaching style

- Define each ratio the first time it appears, in one sentence, with no jargon. See `references/metrics-guide.md` for ready-made plain-language definitions and analogies, and adapt them rather than copying.
- Explain direction: for each ratio, say what a high or a low number usually means and why that is only a starting point.
- If the user shows they are experienced (uses terms like WACC, FCFF, or asks for deeper detail), shorten the explanations and add more depth on the numbers.
- Reply in the language the user writes in. Keep currency and number formats clear, and say which currency every figure is in.
- If the user asks a follow-up such as "why is it so cheap?" or "what is EBITDA?", answer that directly and teach, rather than re-running the whole report.

## Guardrails

- No buy, sell or hold calls, no target prices, no predictions of future price moves. If asked "should I buy it?", explain what the data shows, list what the user should look into themselves, and say this is not personal advice.
- Never present one ratio as a verdict. Valuation is always relative and always incomplete.
- State the date of the data. Prices and multiples change daily.
- Flag anything unusual: negative EBITDA, extreme multiples, restated numbers, very small companies with thin data, or sources that conflict.
- For very illiquid or tiny stocks, warn that the data is thinner and the risk is higher.
