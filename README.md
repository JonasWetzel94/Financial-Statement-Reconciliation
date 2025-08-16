# AppleDot Financial Ratios — End-to-End Excel Ratio Framework with Benchmarks


## Visual Overview
<img width="887" height="228" alt="image" src="https://github.com/user-attachments/assets/646f03df-c484-4198-a866-d93c9afd19af" />

---

**Selected Outputs (Current Year)**  
| Category        | Metric                        | Result |
|---|---|---:|
| Activity        | Cash Conversion Cycle (days)  | **0.6** |
| Liquidity       | Current Ratio                 | **1.01** |
| Solvency        | Debt-to-Equity                | **123%** |
| Profitability   | Gross Profit Margin           | **47.1%** |
| Profitability   | Net Profit Margin             | **3.1%** |
| Valuation       | EPS (USD)                     | **8.94** |
| Valuation       | P/E                           | **1.45** |
| Efficiency      | Total Asset Turnover          | **2.20** |

Metrics calculated from the project’s provided statements and notes.

---

## Case Description
AppleDot Ltd (consumer electronics) engages in the design, manufacture, and sale of devices and services. The task is to evaluate the company’s performance using a robust ratio framework and benchmark the results against industry averages.

---

## Tasks
- Build a reusable **ratio analysis framework** (Activity, Liquidity, Solvency, Profitability, Valuation).  
- **Calculate** current-year ratios from the supplied Income Statement and Balance Sheet.  
- **Benchmark** against industry averages and interpret performance.  
- Add **sanity checks** (e.g., CCC recomputation, leverage reconciliation, P/E × EPS ≈ Price).

---

## Accounting/Analytics Steps
1. **Model setup**: define named ranges/structured references for core inputs (Revenue, COGS, Gross_Profit, Operating_Profit, Net_Income, Cash, Marketable_Securities, Receivables, Inventory, Current_Assets, Current_Liabilities, ST_Debt, LT_Debt, Total_Equity, Avg_Total_Assets, Avg_Equity).  
2. **Compute category blocks**:  
   - *Activity*: DSO, DIO, DPO, CCC, Asset Turnover.  
   - *Liquidity*: Current, Quick, Cash ratios.  
   - *Solvency*: D/E, Debt-to-Capital, Financial Leverage.  
   - *Profitability*: Gross, Operating, Net margins; ROE.  
   - *Valuation*: EPS, P/E, price back-check.  
3. **Benchmark layer**: store industry averages and compute gaps vs. AppleDot.  
4. **Quality controls**: re-derive CCC from components; recompute Debt-to-Capital from D/E; validate P/E × EPS ≈ Share Price.

---

## Trial Balance / Data Summary (table + totals/checks)
**Key Inputs Used for Ratios (Currency: USD ‘000 unless noted)**

| Input                               | Value       |
|---|---:|
| Revenue                             | 28,986,035 |
| Gross Profit                        | 13,652,454 |
| Operating Profit                    | 1,128,069  |
| Net Income                          | 894,178    |
| Current Assets                      | 7,816,092  |
| Current Liabilities                 | 7,730,390  |
| Cash + Marketable Securities + Receivables | 7,454,799  |
| Cash + Marketable Securities        | 2,146,661  |
| Short-Term Debt                     | 1,347,357  |
| Long-Term Debt                      | 1,398,041  |
| Total Debt                          | 2,745,398  |
| Total (Avg) Equity                  | 2,225,347  |
| Average Total Assets                | 13,174,034 |
| Shares Outstanding (common)         | 100,000    |
| Share Price (USD)                   | 12.95      |

Numbers sourced from the provided statements/notes.

**Checks**  
- Debt-to-Capital ≈ 2,745,398 / (2,745,398 + 2,225,347) = **55%** ✅  
- P/E × EPS ≈ **1.45 × 8.94 = 12.95** (≈ price) ✅  
- CCC = **67 + 8.6 − 75 = 0.6 days** ✅

---

## Financial Statements / Results (key numbers)
**Margins & Returns**  
- GPM = 13,652,454 / 28,986,035 = **47.1%**  
- OPM = 1,128,069 / 28,986,035 = **3.9%**  
- NPM = 894,178 / 28,986,035 = **3.1%**  
- ROE ≈ 894,178 / 2,225,347 = **40.2%**  
- Financial Leverage ≈ 13,174,034 / 2,225,347 = **5.92×**  
- Total Asset Turnover = 28,986,035 / 13,174,034 = **2.20×**

**Liquidity & Capital Structure**  
- Current Ratio = 7,816,092 / 7,730,390 = **1.01**  
- Quick Ratio = 7,454,799 / 7,730,390 = **0.96**  
- Cash Ratio = 2,146,661 / 7,730,390 = **0.28**  
- D/E = (1,347,357 + 1,398,041) / 2,225,347 = **123%**  
- Debt-to-Capital = **55%** (as above). :contentReference[oaicite:7]{index=7}

**Working Capital Cycle**  
- DSO = **67 days**; DIO = **8.6 days**; DPO = **75 days** → CCC = **0.6 days**.

**Valuation**  
- EPS = 894,178 / 100,000 = **8.94**; P/E = 12.95 / 8.94 = **1.45**.

---

## Mapping / Logic (formulas used)
**Activity**  
- Receivables Turnover = Revenue / Avg Receivables; `DSO = 365 / ReceivablesTurnover = 67`  
- Inventory Turnover = COGS / Avg Inventory; `DIO = 365 / InventoryTurnover = 8.6`  
- Payables Turnover = Purchases (or COGS adj.) / Avg Payables; `DPO = 365 / PayablesTurnover = 75`  
- `CCC = DSO + DIO − DPO = 0.6`  
- `Asset_Turnover = Revenue / Avg_Total_Assets = 2.20`

**Liquidity**  
- `Current = Current_Assets / Current_Liabilities = 1.01`  
- `Quick = (Cash + Marketable + Receivables) / Current_Liabilities = 0.96`  
- `Cash_Ratio = (Cash + Marketable) / Current_Liabilities = 0.28`

**Solvency**  
- `D_E = (ST_Debt + LT_Debt) / Total_Equity = 123%`  
- `Debt_to_Cap = Total_Debt / (Total_Debt + Total_Equity) = 55%`  
- `Leverage = Avg_Total_Assets / Avg_Equity = 5.92×`

**Profitability & Valuation**  
- `GPM = Gross_Profit / Revenue = 47.1%`  
- `OPM = Operating_Profit / Revenue = 3.9%`  
- `NPM = Net_Income / Revenue = 3.1%`  
- `ROE ≈ Net_Income / Avg_Equity = 40.2%`  
- `EPS = Net_Income / Shares = 8.94`  
- `P_E = Price / EPS = 1.45` (price back-check passes).

---

## Industry Benchmark (selected)
| Metric                    | AppleDot | Industry Avg | Comment |
|---|---:|---:|---|
| DSO (days)                | 67.0 | 60.0 | Slightly slower collections |
| DIO (days)                | 8.6  | 15.3 | Faster inventory turns |
| DPO (days)                | 75.0 | 60.0 | Slower payments |
| CCC (days)                | 0.6  | 15.3 | Strong cash cycle |
| Current Ratio             | 1.01 | 1.40 | Lower liquidity buffer |
| Quick Ratio               | 0.96 | 1.00 | Near parity |
| Cash Ratio                | 0.28 | 0.50 | Less immediate liquidity |
| D/E                       | 123% | 55%  | More leveraged |
| Debt-to-Capital           | 55%  | 28%  | Higher leverage mix |
| Gross Margin              | 47.1%| 29.5%| Strong product margins |
| Operating Margin          | 3.9% | 13.2%| Higher OPEX burden |
| Net Margin                | 3.1% | 9.8% | Lower bottom-line yield |
| ROE                       | 40.2%| 15.0%| High equity productivity |
| EPS                       | 8.94 | 5.83 | Higher earnings per share |
| P/E                       | 1.45 | 5.5  | Lower market multiple |
| Share Price (USD)         | 12.95| 32.1 | Lower absolute price |

Benchmarks as provided with the task; interpretations follow directly from these comparisons.

---

## How I Built It
- **Tools**: Excel (named ranges, structured tables, Data Validation), formula auditing, cross-checks.  
- **Design**: category-based blocks with inputs → calculations → benchmarks; one-click print area for a recruiter-friendly summary.  
- **Example formulas (Excel)**:
  - `=Gross_Profit/Revenue` → GPM  
  - `=365 / (Revenue/AVERAGE(Receivables_Open,Receivables_Close))` → DSO  
  - `=(Cash + Marketable_Securities + Receivables) / Current_Liabilities` → Quick Ratio  
  - `=(ST_Debt + LT_Debt) / Total_Equity` → D/E  
  - `=Net_Income / Shares_Outstanding` → EPS  
  - `=Price / EPS` → P/E  
- **Validation**: CCC recomputation; leverage & capital mix reconciliations; P/E × EPS ≈ price.

---

## What I Learned
- Building a **portable ratio framework** that cleanly separates inputs, calculations, and benchmarks.  
- The **tension between high gross margins and low operating margins** (cost structure focus).  
- How **leverage amplifies ROE** and risks; why liquidity backstops matter despite strong CCC.

---

## Quick Skills Snapshot
- Financial statement **ratio modeling** (Activity, Liquidity, Solvency, Profitability, Valuation).  
- **Excel modeling** with named ranges, structured references, and audit-ready checks.  
- **Benchmark analysis**
- **use of pivot tables**

