# Credit Risk Data Dictionary

This document describes the dataset fields used in the credit risk modeling project.  
The ratios are drawn from classical bankruptcy prediction models (e.g., Altman Z-Score) and are widely used in credit risk analysis.

---

## Core Identifiers

- **Firm_ID**  
  *Integer.* Unique identifier for each firm in the dataset.

- **Year, Month, Day**  
  *Integers.* Calendar date associated with the financial record.

---

## Target Variable

- **Default**  
  *Binary (0 or 1).* Indicator of whether the firm defaulted within the given period.  
  - `0` → No default  
  - `1` → Default occurred

---

## Predictor Variables (Financial Ratios)

- **WC/TA** → *Working Capital / Total Assets*  
  - **Definition:** Working Capital = Current Assets – Current Liabilities.  
  - **Purpose:** Liquidity ratio; measures ability to cover short-term obligations.  
  - **Range:** Can be positive or negative.  
  - **Notes:** Negative values signal current liabilities exceed current assets — a red flag for distress.

- **RE/TA** → *Retained Earnings / Total Assets*  
  - **Definition:** Retained Earnings = cumulative net income – dividends paid.  
  - **Purpose:** Profitability ratio; reflects the extent assets are financed through retained profits.  
  - **Range:** Can be positive or negative.  
  - **Notes:** Negative values occur when cumulative losses exceed profits.

- **EBIT/TA** → *Earnings Before Interest and Taxes / Total Assets*  
  - **Definition:** Operating income relative to total assets.  
  - **Purpose:** Efficiency ratio; shows the firm’s ability to generate operating profits from assets.  
  - **Range:** Can be positive or negative.  
  - **Notes:** Negative EBIT/TA indicates operating losses.

- **ME/TL** → *Market Value of Equity / Total Liabilities*  
  - **Definition:** Market Equity = Share Price × Shares Outstanding.  
  - **Purpose:** Solvency ratio; compares market equity value to total liabilities.  
  - **Range:** Should be ≥ 0 (cannot be negative by definition).  
  - **Notes:** Near-zero values indicate little equity buffer against debt.

- **S/TA** → *Sales / Total Assets*  
  - **Definition:** Revenue relative to total assets.  
  - **Purpose:** Asset turnover ratio; measures how efficiently assets generate sales.  
  - **Range:** Should be ≥ 0.  
  - **Notes:** Low values signal weak efficiency or underutilized assets.

---

## Summary of Valid Ranges

| Variable | Negative Values Allowed? | Interpretation if Negative |
|----------|--------------------------|----------------------------|
| WC/TA    | ✅ Yes                   | Current liabilities exceed current assets |
| RE/TA    | ✅ Yes                   | Accumulated losses exceed profits |
| EBIT/TA  | ✅ Yes                   | Operating losses |
| ME/TL    | ❌ No                    | Should always be ≥ 0 |
| S/TA     | ❌ No                    | Should always be ≥ 0 |

---

📌 **Usage Note:**  
Negative values (where permitted) are **informative signals** in credit risk modeling. They often precede financial distress and contribute to default prediction.
