# Calculation Methodology

> This document explains exactly how every scenario in this repository is calculated. Transparency is a core principle of this project.

Full interactive methodology: [fomodejavu.com/methodology](https://fomodejavu.com/methodology/)

---

## Core Calculation Formula

The fundamental question every scenario answers is:

```
Final Value = Initial Shares × Split-Adjusted Price Today
            (+ Reinvested Dividends, if DRIP = true)
```

Where:

```
Initial Shares = Initial Investment (USD) ÷ Adjusted Close Price on Scenario Date
```

---

## Stock Splits

Stock splits **do not change the underlying value** of a holding, but they do change share counts and price per share. We handle splits retroactively:

```
Split-Adjusted Shares = Initial Shares × Product of All Split Ratios After Purchase Date
```

**Example — Amazon (AMZN):**

| Date | Split | Cumulative Multiplier |
|------|-------|-----------------------|
| 1997-05-15 | Purchase: 510.2 shares | 1× |
| 1998-06-02 | 2:1 split | 2× → 1,020.4 shares |
| 1999-01-05 | 3:1 split | 6× → 3,061.2 shares |
| 1999-09-02 | 2:1 split | 12× → 6,122.4 shares |
| 2022-06-06 | 20:1 split | 240× → 122,448 shares |

We use the **split-adjusted (historical) price** on the purchase date to avoid double-counting.

---

## Dividends

### DRIP Off (default for growth stocks)
Dividends are **excluded**. The scenario shows only price appreciation. This is the correct approach for stocks that paid no dividends (e.g., Amazon, Tesla, early Alphabet).

### DRIP On (default for dividend scenarios)
Dividends are **reinvested** on the ex-dividend date at the closing price on that date. Each reinvestment purchase is tracked:

```
New Shares Per Dividend = (Shares Held × Dividend Per Share) ÷ Price on Ex-Dividend Date
```

Total shares compound over time as each dividend buys fractional new shares.

For dividend scenarios, we use **adjusted close prices** which already account for dividends in the price series when provided by data vendors. We cross-check with raw DRIP calculations where possible.

---

## Inflation Adjustment

### Nominal (default)
All values are shown in **current nominal USD** unless labeled `inflation_adjusted: true`.

### Real (CPI-adjusted)
When inflation adjustment is applied, we use the US Consumer Price Index (CPI-U, seasonally unadjusted) from the Bureau of Labor Statistics:

```
Real Value = Nominal Value × (CPI Today ÷ CPI on Scenario Date)
```

This answers: *"What would that money be worth in today's purchasing power?"*

---

## Non-Trading Days

If a scenario date falls on a weekend or US market holiday, we shift to the **next available trading day**.

| Input Date | Adjustment |
|------------|------------|
| Saturday | → Monday |
| Sunday | → Monday |
| Federal Holiday | → Next trading day |
| Christmas (Mon) | → Dec 26 or next open day |

---

## Cryptocurrency Scenarios

Crypto markets trade **24 hours a day, 7 days a week**. We use:
- **Closing price at 00:00 UTC** on the scenario date
- Price data from aggregated exchange sources
- No split adjustments (crypto does not split in the traditional sense)
- No dividend payments

Crypto scenarios carry an additional **extreme volatility warning**. A $1,000 investment in Bitcoin in 2012 would have passed through multiple 80%+ drawdowns before reaching current values. The scenario shows the *theoretical hold-to-today* outcome, which required surviving those drawdowns.

---

## Dollar-Cost Averaging (DCA) Scenarios

For recurring investment scenarios:

```
For each investment period:
  Shares Purchased = Periodic Investment Amount ÷ Adjusted Close on That Date
  
Total Shares = Sum of all periodic share purchases
Final Value = Total Shares × Current Price
```

We use the **first trading day of each period** (month, year) for simplicity.

---

## CAGR Formula

All scenarios report Compound Annual Growth Rate (CAGR):

```
CAGR = (Final Value ÷ Initial Investment) ^ (1 ÷ Years Held) − 1
```

---

## Data Sources

See [`DATA_SOURCES.md`](DATA_SOURCES.md) for the full list of data providers.

Primary sources used:
- Adjusted close prices from established financial data APIs
- Dividend history from verified financial databases
- CPI data from the US Bureau of Labor Statistics
- Crypto price history from aggregated exchange data

---

## Limitations

1. **Point-in-time approximation**: Scenarios assume the full amount is invested at the opening of the scenario date. Real investors would have bought at ask prices with commissions.
2. **Taxes excluded**: No capital gains, dividend tax, or wash-sale rules are modeled.
3. **Commissions excluded**: Historical brokerage commissions (which were significant pre-2000) are not included.
4. **Liquidity assumed**: We assume the investor could buy any quantity at the stated price, which may not be true for very early-stage assets.
5. **Hindsight bias**: These scenarios were chosen because they produced memorable outcomes. The base rate of random stock picks is much lower than headline FOMO numbers suggest.

These limitations are discussed in depth at [fomodejavu.com/methodology](https://fomodejavu.com/methodology/).

---

## Reproducibility

Every scenario JSON file includes:
- `scenario_date`: exact purchase date used
- `price_on_date_usd`: price used for the calculation
- `splits`: complete split history applied
- `last_updated`: when values were last refreshed
- `calculator_url`: link to reproduce in real-time

If you find a discrepancy, please [open an issue](../../issues).
