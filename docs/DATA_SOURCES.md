# Data Sources

This file documents where all historical price, dividend, inflation, and cryptocurrency data originates.

Full methodology: [fomodejavu.com/methodology](https://fomodejavu.com/methodology/)

---

## Equity Price Data (Stocks & ETFs)

**Primary source:** Adjusted close prices from financial data providers that aggregate exchange data from NYSE, NASDAQ, and CBOE.

Adjusted close prices account for:
- Cash dividends (dividend adjustment factor)
- Stock splits and reverse splits
- Rights offerings and spin-offs (where applicable)

**Validation:** Cross-referenced against SEC EDGAR filings for split history and dividend announcements.

---

## Dividend Data

**Source:** Historical dividend records from financial data vendors, cross-referenced with SEC filings (Form 8-K) and company investor relations pages.

We record:
- **Ex-dividend date** (the date used for DRIP reinvestment calculations)
- **Dividend per share** (unadjusted for splits at time of payment)
- **Payment date** (informational only; not used in calculations)

---

## Cryptocurrency Price Data

**Sources:**
- Aggregated exchange data (volume-weighted average across major exchanges)
- Historical data validated against multiple independent archive sources
- UTC midnight closing prices used as reference

**Coverage:** Bitcoin (BTC), Ethereum (ETH), and other major assets.

**Limitation:** Early Bitcoin pricing (pre-2013) is based on sparse exchange records and should be treated as approximate.

---

## Inflation / CPI Data

**Source:** US Bureau of Labor Statistics (BLS)
- Series: CPI-U (Consumer Price Index for All Urban Consumers)
- Seasonal adjustment: Unadjusted
- Update cadence: Monthly, with ~1 month lag
- URL: https://www.bls.gov/cpi/

---

## Stock Split History

**Primary source:** Exchange records and company announcements.

**Validation:** Cross-referenced with SEC EDGAR 8-K filings for each split event.

All splits in this repo are stored explicitly in each scenario's `splits` array for full transparency and reproducibility.

---

## Update Cadence

| Data Type | Update Frequency |
|-----------|-----------------|
| Scenario "value today" | Quarterly |
| Historical prices | Static (fixed to scenario date) |
| CPI/inflation | Quarterly |
| Crypto prices | Quarterly |
| Dividend history | Annual |

Current prices for any scenario can always be recalculated in real-time at [fomodejavu.com](https://fomodejavu.com/).

---

## Reporting Discrepancies

If you find a data error — wrong split, wrong price, missing dividend — please:

1. Open a GitHub Issue with the scenario file name
2. Provide your source (SEC filing URL, exchange record, etc.)
3. We will review and correct within 30 days

See [`CONTRIBUTING.md`](../CONTRIBUTING.md) for full contribution guidelines.
