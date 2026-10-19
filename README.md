# Beginner Stock Analysis: a skill for Claude

A free [Claude](https://claude.ai) skill that turns a **stock name, ticker or ISIN** into a short, plain-language valuation snapshot, built for inexperienced investors and designed to teach as it goes.

## What you get

For any listed company, Claude produces a compact report with:

- **Snapshot of key ratios**: EV/EBITDA, P/E, P/B, EV/Sales, FCF yield, dividend yield, net debt/EBITDA, each with a one-line plain-English explanation
- **Versus its own history**: where the current multiple sits compared with its 5- to 10-year range
- **Versus peers**: 3 to 5 comparable companies and the peer median
- **How to read this**: a balanced interpretation, with no buy/sell advice
- **What the ratios do not tell you**: debt, growth, business quality and other blind spots
- **Learn box**: one concept explained with an everyday analogy

The skill picks ratios that fit the business (for example, no EV/EBITDA for banks) and explains why. Every figure should carry a source and a date; if a number cannot be found, Claude says so instead of guessing.

## Install

1. Download `beginner-stock-analysis.skill` from the [latest release](../../releases/latest).
2. In Claude, open **Settings → Capabilities → Skills** (on some versions: **Customize → Skills**) and upload the file.
3. Make sure the skill is switched on.

## Use

Start a new chat, turn on **web search**, and ask something like:

- "Analyse Siemens"
- "Is DE0007164600 cheap or expensive?"
- "Compare the valuation of Adidas with its peers"
- "Explain EV/EBITDA using Nvidia as an example"

You do not need to name the skill; Claude loads it when your request matches.

## Limitations

- Data quality depends on what Claude can find through web search or any financial-data tools you have connected. Historical multiples and peer figures are sometimes incomplete or approximate, and the skill labels them as such.
- Always verify important figures against the company's own reports.
- Not suitable for bank, insurer or REIT valuation beyond the basics.

## Disclaimer

This project is for **educational purposes only** and is **not investment advice**. It does not recommend buying, selling or holding any security. Figures may be wrong or out of date. You are responsible for your own investment decisions.

## Contributing

Issues and pull requests are welcome, especially better peer-selection rules, sector-specific guidance and translations.

## License

[MIT](LICENSE)
