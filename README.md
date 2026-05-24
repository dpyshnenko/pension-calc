# The Dutch ETF Pension Plan Calculator

A standalone, interactive, single-file HTML calculator designed for Dutch retail investors to model their retirement using a *pensioenrekening* (pension account, e.g., via DEGIRO, Meesman, or Brand New Day) alongside the state pension (AOW).

## Overview

This tool provides a two-part model based on the **2026 Dutch tax rules**:
1. **The Accumulation Phase:** Calculates how much your pension pot will grow over your working life by combining your deposits, the reinvested Box 1 tax refunds (based on your *jaarruimte*), and estimated market growth.
2. **The Payout Phase:** Calculates your actual net monthly income in retirement when combining your fixed-duration annuity (*lijfrente*) and the Dutch state pension (*AOW*), accounting for AOW-age tax brackets.

## Features

* **Interactive Sliders:** Adjust your current age, retirement age, income, and contributions to instantly see the impact on your final pot.
* **Jaarruimte Awareness:** The calculator automatically limits your tax-deductible contributions to your statutory *jaarruimte* (annual margin). If you contribute more than is tax-deductible, it throws a warning.
* **Tax Refund Reinvestment:** A core feature of this model is that it automatically reinvests the tax refund you receive from the Belastingdienst (35.82% or 49.50% depending on income) back into the pension pot, demonstrating the power of the "rate arbitrage" between working-age and retirement-age tax brackets.
* **Automatic Payout Sync:** The final pot size from the accumulation phase automatically flows into the payout phase to give you a realistic estimate of your net monthly income.
* **Visualizations:** Includes a stacked area chart (using Chart.js) for accumulation over time, and a dynamic horizontal bar chart for the retirement income split.

## How the Math Works

### Section I: Accumulation
* **Jaarruimte Formula (2026):** `30% × (Gross Income - €19,172)`, capped at a maximum income of €137,800. *(Note: Assumes Factor A = 0, meaning no employer pension accrual).*
* **Tax Brackets (Working Age):** Contributions within the jaarruimte are deducted at 35.82% (up to €38,883) or 49.50% (above €38,883).
* **Fees:** The model automatically deducts a 0.20% annual fee (simulating DEGIRO's pensioenrekening fee) calculated monthly.

### Section II: Payout
* **Annuity Calculation:** The final pot is converted into an ordinary fixed-duration annuity that spends the pot down to zero over your chosen payout duration (e.g., 20 years).
* **AOW (State Pension):** Includes 2026 gross amounts plus *vakantiegeld* (holiday pay). Adjusts dynamically based on whether you are single or living with a partner.
* **Tax Brackets (AOW Age):** The combined gross income (AOW + lijfrente) is taxed using the lower retirement brackets: 17.92% (up to €38,883), 37.56% (up to €78,426), and 49.50% (above). 

## How to Use

Simply open the `index.html` (or `dutch-pension-calculator.html`) file in any modern web browser. No local server or build process is required. 

## Disclaimer

**This is a model, not financial advice.**
The calculator makes simplifying assumptions (such as constant real income, Factor A = 0, and the exclusion of *heffingskortingen* / tax credits which usually lower actual tax burdens further). Always verify your actual *jaarruimte* via [belastingdienst.nl](https://www.belastingdienst.nl) and consult a certified financial advisor before making retirement decisions. Past market performance does not guarantee future returns.
