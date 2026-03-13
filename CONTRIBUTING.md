# Contributing to Historical Investment Scenarios

Thank you for your interest in contributing. This project thrives on accurate, educational scenario data. Here's how to contribute effectively.

---

## Types of Contributions Welcome

### ✅ Accepted
- New historically significant investment scenarios (IPOs, market bottoms, famous inflection points)
- Corrections to existing scenario data (wrong price, missing split, incorrect date)
- New notebook examples using existing data
- Documentation improvements
- Additional inflation or purchasing power scenarios (non-US CPI sources welcome)
- International market scenarios (LSE, TSX, Nikkei, etc.)

### ❌ Not Accepted
- Speculative future projections
- Scenarios without verifiable historical price data
- Duplicate scenarios
- AI-generated data without verification
- Scenarios for assets with no meaningful price history (very low liquidity, obscure tokens)
- Any content that could be construed as financial advice

---

## Adding a New Scenario

### Step 1: Check for Duplicates

Search existing scenarios in `/scenarios/` before adding. Filter by ticker or date range.

### Step 2: Use the Correct File Format

Copy this template and fill it out completely:

```json
{
  "scenario_id": "ticker-brief-description-year",
  "title": "$X in Asset Name at Event (Year)",
  "description": "Full description of what this scenario represents and why it's historically significant.",
  "ticker": "TICKER",
  "asset_name": "Full Asset Name",
  "asset_type": "stock | etf | crypto | inflation | other",
  "scenario_date": "YYYY-MM-DD",
  "initial_investment_usd": 1000,
  "price_on_date_usd": 0.00,
  "shares_purchased": 0.0,
  "splits": [],
  "total_split_multiplier": 1,
  "split_adjusted_shares": 0.0,
  "dividends_reinvested": false,
  "dividend_note": "Explanation of dividend treatment.",
  "inflation_adjusted": false,
  "value_today_usd": 0,
  "total_return_pct": 0,
  "cagr_pct": 0.0,
  "years_held": 0,
  "last_updated": "YYYY-MM-DD",
  "tags": [],
  "educational_note": "Key insight for educators, writers, or students.",
  "calculator_url": "https://fomodejavu.com/?ticker=TICKER&date=YYYY-MM-DD&amount=1000",
  "source": "https://fomodejavu.com/methodology/"
}
```

### Step 3: Verify Your Data

Required verifications before submitting:
- [ ] Price on scenario date: verified against at least one financial data source
- [ ] All stock splits applied correctly (check SEC EDGAR 8-K filings)
- [ ] Dividend treatment clearly stated
- [ ] CAGR formula correct: `(FinalValue/InitialInvestment)^(1/Years) - 1`
- [ ] `scenario_id` follows the pattern: `{ticker-lower}-{brief-description}-{year}`
- [ ] File placed in correct subdirectory (`stocks/`, `crypto/`, `etf/`, etc.)
- [ ] File named: `{ticker-lower}-{description}-{year}-{amount}usd.json`

### Step 4: Update the Master CSV

Add your scenario as a new row in `data/scenarios-master.csv`. Follow the existing column format exactly.

### Step 5: Open a Pull Request

- Title: `[Scenario] TICKER — Brief Description (YEAR)`
- Description: Explain the scenario and link your data source
- One scenario per PR for clean review history

---

## Reporting Data Errors

If you find an error in existing scenario data:

1. Open an Issue using the **Data Error** template
2. Specify the file name and incorrect field
3. Provide the correct value with a source (SEC filing URL, verified price source, etc.)
4. We aim to review corrections within 14 days

---

## Code of Conduct

- Be respectful and constructive
- Cite your data sources
- Don't submit data you can't verify
- Don't use this project to promote specific investments or financial products

---

## Questions?

Open an Issue with the **Question** label or visit [fomodejavu.com](https://fomodejavu.com/) for methodology details.
