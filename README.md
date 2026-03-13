# 📈 Historical Investment Scenarios

> **Open educational dataset of "What if I had invested…" scenarios — stocks, ETFs, crypto, dividends, and inflation — with reproducible data, methodology, and embeddable tools.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Scenarios](https://img.shields.io/badge/Scenarios-30%2B-blue.svg)](scenarios/)
[![Data Format](https://img.shields.io/badge/Format-JSON%20%7C%20CSV-orange.svg)](data/)
[![Website](https://img.shields.io/badge/Calculator-fomodejavu.com-purple.svg)](https://fomodejavu.com/)

---

**Live calculator & case studies →** [fomodejavu.com](https://fomodejavu.com/)
**Methodology & data sources →** [fomodejavu.com/methodology](https://fomodejavu.com/methodology/)

---

## What Is This?

This repository is a free, open collection of **historical investment scenario data** built for:

- 📚 **Educators** teaching compounding, risk, and opportunity cost
- ✍️ **Writers & journalists** who need verified "what if" examples
- 🧑‍💻 **Developers** building personal finance tools and calculators
- 📊 **Researchers** studying behavioral finance and FOMO-driven decisions
- 🧑‍🎓 **Students** learning about markets, inflation, and long-term investing

Every scenario answers one question: *"What would $1,000 (or another amount) invested on a specific date be worth today?"*

The data, assumptions, and methodology are fully transparent. No black boxes.

---

## 📂 Repository Structure

```
historical-investment-scenarios/
├── scenarios/
│   ├── stocks/          # Individual stock what-if scenarios (Amazon, Apple, Tesla, NVIDIA…)
│   ├── crypto/          # Cryptocurrency scenarios (Bitcoin, Ethereum…)
│   ├── etf/             # Index fund & ETF scenarios (S&P 500, NASDAQ…)
│   ├── dividends/       # Dividend reinvestment (DRIP) scenarios
│   ├── inflation/       # Inflation & purchasing power examples
│   └── annual/          # Recurring investment scenarios (DCA, latte factor…)
├── data/
│   ├── scenarios-master.csv     # All scenarios in one flat file
│   └── scenarios-master.json    # All scenarios as JSON array
├── notebooks/
│   ├── 01_getting_started.ipynb
│   ├── 02_dividend_reinvestment.ipynb
│   ├── 03_inflation_adjustment.ipynb
│   └── 04_crypto_volatility.ipynb
├── widgets/
│   └── what-if-widget.html      # Embeddable standalone HTML calculator widget
├── docs/
│   ├── METHODOLOGY.md           # Full calculation methodology
│   ├── DATA_SOURCES.md          # Data sources and update cadence
│   └── ASSUMPTIONS.md           # Key assumptions and limitations
└── .github/
    └── ISSUE_TEMPLATE/          # Templates for contributing scenarios
```

---

## 🚀 Quick Start

### Use the data directly (no code required)

Download [`data/scenarios-master.csv`](data/scenarios-master.csv) and open in Excel, Google Sheets, or any spreadsheet app.

### Use with Python

```python
import pandas as pd

df = pd.read_csv("data/scenarios-master.csv")

# Filter to stock scenarios
stocks = df[df["asset_type"] == "stock"]
print(stocks[["ticker", "scenario_date", "initial_investment_usd", "value_today_usd"]].head(10))
```

### Use a single scenario JSON

```python
import json

with open("scenarios/stocks/amazon-ipo-1997-1000usd.json") as f:
    scenario = json.load(f)

print(f"${scenario['initial_investment_usd']:,.0f} in {scenario['ticker']} on {scenario['scenario_date']}")
print(f"Would be worth ${scenario['value_today_usd']:,.0f} today")
print(f"That's a {scenario['total_return_pct']:.1f}% total return over {scenario['years_held']} years")
```

---

## 📋 Scenario Index

### 🏢 Stocks — What If I Had Invested?

| Scenario | Ticker | Date | $1,000 Invested | Approx. Value Today | CAGR |
|----------|--------|------|-----------------|---------------------|------|
| Amazon IPO | AMZN | 1997-05-15 | $1,000 | ~$2,100,000 | ~38% |
| Apple (iPhone launch) | AAPL | 2007-01-09 | $1,000 | ~$42,000 | ~24% |
| Tesla (post-IPO dip) | TSLA | 2012-01-01 | $1,000 | ~$50,000 | ~55% |
| NVIDIA (pre-AI era) | NVDA | 2015-01-01 | $1,000 | ~$65,000 | ~50% |
| Netflix (post-DVD pivot) | NFLX | 2012-01-01 | $1,000 | ~$18,000 | ~42% |
| Microsoft (Nadella era) | MSFT | 2014-02-04 | $1,000 | ~$18,000 | ~32% |
| Google / Alphabet IPO | GOOGL | 2004-08-19 | $1,000 | ~$55,000 | ~27% |
| Meta IPO | META | 2012-05-18 | $1,000 | ~$11,000 | ~26% |

> 📌 Values are **educational approximations** updated periodically. Use the [live calculator](https://fomodejavu.com/) for real-time figures.

### ₿ Crypto — What If I Had Invested?

| Scenario | Asset | Date | $1,000 Invested | Approx. Value Today | CAGR |
|----------|-------|------|-----------------|---------------------|------|
| Bitcoin (early adopter) | BTC | 2012-01-01 | $1,000 | ~$500,000,000+ | ~150% |
| Bitcoin (post-halving) | BTC | 2016-07-09 | $1,000 | ~$100,000 | ~80% |
| Ethereum launch | ETH | 2015-08-07 | $1,000 | ~$1,200,000 | ~130% |
| Bitcoin (before bull run) | BTC | 2020-01-01 | $1,000 | ~$13,000 | ~90% |

> ⚠️ Crypto scenarios illustrate **extreme volatility**. Past performance is not indicative of future results.

### 📊 ETFs & Index Funds

| Scenario | Asset | Date | $1,000 Invested | Approx. Value Today | CAGR |
|----------|-------|------|-----------------|---------------------|------|
| S&P 500 (2000 peak) | SPY | 2000-01-01 | $1,000 | ~$5,200 | ~9% |
| S&P 500 (2008 bottom) | SPY | 2009-03-09 | $1,000 | ~$9,800 | ~18% |
| NASDAQ-100 (post dot-com) | QQQ | 2003-01-01 | $1,000 | ~$25,000 | ~21% |
| Total Market (20-year hold) | VTI | 2004-01-01 | $1,000 | ~$8,500 | ~12% |

### 💰 Dividends (DRIP Reinvested)

| Scenario | Ticker | Date | $10,000 Invested | Approx. Value Today |
|----------|--------|------|------------------|---------------------|
| Johnson & Johnson | JNJ | 2004-01-01 | $10,000 | ~$85,000 |
| Coca-Cola | KO | 2004-01-01 | $10,000 | ~$55,000 |
| Realty Income (REIT) | O | 2010-01-01 | $10,000 | ~$35,000 |
| Procter & Gamble | PG | 2004-01-01 | $10,000 | ~$75,000 |

### 🔄 Annual Investing (Dollar-Cost Averaging)

| Scenario | Asset | Start | Annual Amount | Approx. Value Today |
|----------|-------|-------|---------------|---------------------|
| $1,000/year in S&P 500 (since 18) | SPY | 2004-01-01 | $1,000 | ~$45,000 |
| Skip the daily latte ($5/day → S&P 500) | SPY | 2014-01-01 | $1,825 | ~$35,000 |
| Max Roth IRA every year | SPY | 2010-01-01 | $5,000–$7,000 | ~$185,000 |
| $100/month regardless of market | VTI | 2010-01-01 | $1,200 | ~$32,000 |

### 🏠 Inflation & Purchasing Power

| Scenario | Year | $1,000 Then | Equivalent Today |
|----------|------|-------------|------------------|
| 1990 purchasing power | 1990 | $1,000 | ~$2,400 |
| 2000 purchasing power | 2000 | $1,000 | ~$1,800 |
| 2010 purchasing power | 2010 | $1,000 | ~$1,400 |
| 2020 purchasing power | 2020 | $1,000 | ~$1,190 |

---

## 🔢 Scenario File Format

Each scenario is a single self-contained JSON file. Example: [`scenarios/stocks/amazon-ipo-1997-1000usd.json`](scenarios/stocks/amazon-ipo-1997-1000usd.json)

```json
{
  "scenario_id": "amzn-ipo-1997",
  "title": "$1,000 in Amazon at IPO (1997)",
  "description": "What $1,000 invested in Amazon on its IPO date would be worth today, with all stock splits accounted for and no dividends (Amazon paid none).",
  "ticker": "AMZN",
  "asset_name": "Amazon.com Inc.",
  "asset_type": "stock",
  "scenario_date": "1997-05-15",
  "initial_investment_usd": 1000,
  "price_on_date_usd": 1.96,
  "shares_purchased": 510.2,
  "splits": [
    { "date": "1998-06-02", "ratio": "2:1" },
    { "date": "1999-01-05", "ratio": "3:1" },
    { "date": "1999-09-02", "ratio": "2:1" },
    { "date": "2022-06-06", "ratio": "20:1" }
  ],
  "split_adjusted_shares": 61224,
  "dividends_reinvested": false,
  "inflation_adjusted": false,
  "value_today_usd": 2100000,
  "total_return_pct": 209900,
  "cagr_pct": 37.8,
  "years_held": 27,
  "last_updated": "2025-01-01",
  "tags": ["ipo", "e-commerce", "cloud", "jeff-bezos", "dot-com-survivor"],
  "educational_note": "Amazon's stock split four times. An investor who bought 510 shares at IPO would hold 61,224 split-adjusted shares today.",
  "calculator_url": "https://fomodejavu.com/?ticker=AMZN&date=1997-05-15&amount=1000",
  "source": "https://fomodejavu.com/methodology/"
}
```

---

## 📐 Methodology Summary

Full methodology is in [`docs/METHODOLOGY.md`](docs/METHODOLOGY.md).

**Key principles:**

| Factor | Treatment |
|--------|-----------|
| Stock splits | All splits are retroactively applied to share counts |
| Dividends | Each scenario states whether dividends are reinvested (DRIP) or excluded |
| Inflation | Scenarios are **nominal by default**; inflation-adjusted variants are labeled |
| Non-trading days | Investment date shifted to next available trading day |
| Crypto weekends | Crypto trades 24/7; exact date prices used |
| Historical prices | Adjusted close prices from verified financial data providers |

For full sources and limitations, see [fomodejavu.com/methodology](https://fomodejavu.com/methodology/).

---

## 🧮 Interactive Calculator

All scenarios in this repo can be explored interactively — with real-time data, custom amounts, and custom dates — at:

**[fomodejavu.com](https://fomodejavu.com/)**

The calculator supports:
- Any US-listed stock or ETF
- Bitcoin, Ethereum, and other major cryptocurrencies
- Custom investment amounts and start dates
- Inflation adjustment toggle
- Dividend reinvestment (DRIP) toggle
- Missed-opportunity (FOMO) framing

---

## 🤝 Contributing

Want to add a scenario? See [`CONTRIBUTING.md`](CONTRIBUTING.md).

**Good scenario ideas:**
- Historical IPOs (Shopify, Airbnb, Snowflake…)
- Country/sector ETFs
- International markets
- Inflation edge cases
- Commodity what-ifs (gold, oil…)

**Not accepted:**
- Speculative future projections
- Scenarios without verifiable historical prices
- Duplicate scenarios already in the dataset

---

## ⚖️ Disclaimer

All data in this repository is for **educational purposes only**. Past performance is not indicative of future results. Nothing here constitutes financial advice. Always consult a licensed financial professional before making investment decisions.

See full methodology and data limitations at [fomodejavu.com/methodology](https://fomodejavu.com/methodology/).

---

## 📄 License

MIT License. Free to use, modify, and distribute with attribution. See [LICENSE](LICENSE).

---

## 🔗 Links

| Resource | URL |
|----------|-----|
| 🌐 Live Calculator | [fomodejavu.com](https://fomodejavu.com/) |
| 📖 Methodology | [fomodejavu.com/methodology](https://fomodejavu.com/methodology/) |
| 📰 Case Studies Blog | [fomodejavu.com/blog](https://fomodejavu.com/blog) |
| 💬 Issues & Ideas | [GitHub Issues](../../issues) |
| 🤝 Contribute | [CONTRIBUTING.md](CONTRIBUTING.md) |

---

*Built and maintained by [FomoDéjàVu](https://fomodejavu.com/) — educational tools for understanding historical investment returns, compounding, and opportunity cost.*
