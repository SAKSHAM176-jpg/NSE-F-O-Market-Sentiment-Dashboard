# NSE-F-O-Market-Sentiment-Dashboard
Market sentiment analysis using NSE F&amp;O participant-wise open interest, combining futures and options positioning into a normalized bullish–bearish score.”

# NSE F&O Market Sentiment Analysis  
Participant-Wise Open Interest Based Model

## Overview

This project implements a **market sentiment analysis engine** using **NSE F&O participant-wise Open Interest data**.  
It infers **Bullish, Bearish, or Neutral** market bias by analyzing how different market participants are positioned in **futures and options**.

Unlike price-based indicators, this model focuses on **actual positioning and capital commitment**, making it more aligned with institutional trading analysis.

The output is designed to be **dashboard-ready**, with clear numerical scores and interpretable visualizations.

---

## Objective

The objective of this project is to:
- Quantify market sentiment using participant positioning
- Compare sentiment across FIIs, DIIs, Proprietary traders, and Retail clients
- Provide a normalized sentiment score suitable for trading dashboards and analytics platforms

---

## Data Source

- NSE Participant-Wise Open Interest (Equity Derivatives)
- Index and Stock Futures and Options
- Official NSE daily CSV files

### Participants Included
- FII – Foreign Institutional Investors  
- DII – Domestic Institutional Investors  
- Pro – Proprietary Traders  
- Client – Retail / Non-Institutional Traders  

---

## Conceptual Framework

Open Interest represents **active positions in the market**.  
By analyzing whether participants are net long or net short in futures and options, we can infer their directional bias and conviction.

Key principles:
- Futures indicate directional intent
- Options reflect hedging and sentiment asymmetry
- Institutional positioning often leads price action

---

## Methodology

### Net Futures Position

\[
\text{Net Futures} =
(\text{Future Index Long} + \text{Future Stock Long})
-
(\text{Future Index Short} + \text{Future Stock Short})
\]

---

### Net Options Position

**Net Call Open Interest**

\[
(\text{Index Call Long} + \text{Stock Call Long})
-
(\text{Index Call Short} + \text{Stock Call Short})
\]

**Net Put Open Interest**

\[
(\text{Index Put Long} + \text{Stock Put Long})
-
(\text{Index Put Short} + \text{Stock Put Short})
\]

---

### Futures Bias (Normalized)

\[
\text{Futures Bias} =
\frac{\text{Net Futures}}
{\sum |\text{Net Futures across all participants}|}
\]

Range: −1 to +1

---

### Options Bias (Normalized)

\[
\text{Option Bias} = \text{Net Put OI} - \text{Net Call OI}
\]

\[
\text{Normalized Option Bias} =
\frac{\text{Option Bias}}
{\text{Net Put OI} + \text{Net Call OI}}
\]

Range: −1 to +1

---

### Final Participant Sentiment Score

\[
\text{Participant Score} =
0.6 \times \text{Futures Bias}
+
0.4 \times \text{Normalized Option Bias}
\]

Futures are weighted higher due to stronger directional conviction.

---

### Sentiment Classification

| Score Range | Interpretation |
|------------|---------------|
| > +0.20 | Bullish |
| −0.20 to +0.20 | Neutral |
| < −0.20 | Bearish |

---

## Visual Outputs

### Participant-Wise Sentiment Chart
- Horizontal bar chart
- Score range from −1 to +1
- Bearish, neutral, and bullish scale zones
- Color-coded participant bars

### Overall Market Sentiment Gauge
- Aggregated market sentiment score
- Visual scale with clear thresholds
- Suitable for dashboard summary cards

## Output

- Console output containing:
  - Participant-wise sentiment scores
  - Bullish / Bearish / Neutral labels
- Two visualizations:
  - Participant sentiment comparison
  - Overall market sentiment gauge

---

## Use Cases

- Trading and investment dashboards
- Institutional flow and positioning analysis
- Market regime identification
- Derivatives market education
- Sentiment-based strategy research

---

## Limitations

- Based on end-of-day Open Interest data
- Does not capture intraday position changes
- Sentiment does not imply short-term price prediction

---

## Disclaimer

This project is intended for educational and analytical purposes only.  
It does not constitute financial or investment advice.  
Market participation involves risk.

---

## Future Enhancements

- Day-over-day sentiment change analysis
- Index-only and stock-only sentiment separation
- Volatility-adjusted weighting
- Confidence and strength metrics
- REST API for real-time dashboards
- Backtesting against NIFTY and BANKNIFTY



## Author

**Saksham Kumar**  
Finance and Analytics  
IIT Ropar  



