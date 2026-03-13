# Assumptions & Limitations

Understanding what these scenarios **do not model** is as important as understanding what they do.

---

## What These Scenarios Model

✅ Historical price appreciation (split-adjusted)  
✅ Dividend reinvestment (where `drip: true`)  
✅ Inflation adjustment (where `inflation_adjusted: true`)  
✅ Compound growth over time  
✅ Dollar-cost averaging (for DCA scenarios)  

---

## What These Scenarios Do NOT Model

### 1. Taxes
Capital gains taxes are not deducted. In the US, long-term capital gains rates (0%, 15%, or 20%) would significantly reduce take-home returns on most scenarios. State taxes are also excluded.

### 2. Brokerage Commissions
Pre-2013, brokerage commissions of $5–$30 per trade were common. For small investments (e.g., $1,000), a $30 commission represented a 3% immediate loss. Our scenarios assume zero commissions.

### 3. Bid-Ask Spreads
We use the adjusted **closing price** as the purchase price. Real investors pay the **ask price**, which is typically slightly higher.

### 4. Behavioral Realities
These scenarios assume the investor:
- **Held through every crash** (Amazon fell 95% during the dot-com bust)
- **Never panic-sold** (Bitcoin fell 80%+ multiple times)
- **Never rebalanced** (which may be suboptimal in practice)
- **Invested the full amount on day one** (lump-sum, not averaging in)

Most real investors would not have held through these drawdowns. The scenarios represent the **theoretical maximum** outcome for a perfect buy-and-hold strategy.

### 5. Survivorship Bias
The scenarios in this repo were selected because they produced notable outcomes. For every Amazon, there are thousands of companies that went to zero. These scenarios do not represent the average investor experience.

### 6. Currency Risk
All scenarios are denominated in USD. Non-US investors would have experienced currency gains or losses on top of the equity return.

### 7. Opportunity Cost
These scenarios compare "investing in X" vs. "holding cash." They do not model alternative investments (bonds, real estate, etc.) or the impact of not having liquidity.

---

## The Hindsight Problem

**These scenarios are selected with perfect hindsight.** Nobody in 1997 knew Amazon would survive the dot-com crash and become the dominant e-commerce platform. Nobody in 2012 knew Bitcoin would achieve the market cap it has today.

Knowing the outcome, these scenarios feel obvious. They were not obvious at the time.

**The purpose of these scenarios is educational** — to illustrate the mechanics of compounding, the power of long holding periods, and the cost of inaction — **not** to suggest these returns are replicable.

---

## Disclaimer

Nothing in this repository constitutes financial advice. All scenarios are for educational purposes only. Past performance is not indicative of future results.

For more context on methodology and limitations, visit [fomodejavu.com/methodology](https://fomodejavu.com/methodology/).
