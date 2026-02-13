# intern_primetrade.ai

# 📊 Hyperliquid Trader Behavior & Market Sentiment Analysis

## 🚀 Project Overview
This project explores the intersection of **market psychology (Fear & Greed Index)** and **on-chain execution data** from the Hyperliquid DEX. By merging Bitcoin sentiment data with granular trader performance metrics, I have identified specific behavioral archetypes and risk patterns that differentiate "Market Survivors" from "Market Liquidity."

### 🎯 Key Objective
To determine if market sentiment is a leading indicator of trader failure (drawdowns) or success (PnL) and to propose data-driven trading rules to optimize performance.

---

## 🛠️ Methodology & Data Pipeline (Part A)
The analysis was conducted in three distinct phases:

1.  **Data Alignment:** Standardized timestamps across the Fear/Greed Index and Hyperliquid trade logs to a unified `YYYY-MM-DD` format.
2.  **Feature Engineering:** Generated critical performance indicators:
    * **Win Rate:** Ratio of profitable closed positions.
    * **Adjusted PnL:** Net profit/loss per trade after accounting for fees (Ref: Cell 93).
    * **Activity Metrics:** Daily trade frequency and average position size (USD).
3.  **Segmentation:** Classified the dataset into behavioral cohorts (High vs. Low Leverage, Frequent vs. Infrequent) to isolate "Alpha" generating behaviors.

---

## 📈 Strategic Insights (Part B)

| Insight | Sentiment Context | Evidence (Data Point) |
| :--- | :--- | :--- |
| **The Fear Paradox** | Extreme Fear | Avg trades/day spike to **2,106** (vs. ~740 in Greed). |
| **Tail-Risk Trap** | Greed | Max Drawdown of **-$358,963** (4.6x higher than Fear). |
| **Execution Efficiency** | Agnostic | **Infrequent** traders outperformed Frequent by **128%** in PnL. |

### 1. The "Fear" Profitability Paradox
Contrary to retail intuition, **Extreme Fear** periods are the most active and profitable for the sampled traders. 
> **Finding:** Fear drives conviction. Traders deploy significantly larger capital (**$7,743 average**) when the market is "blood in the streets," effectively providing liquidity when it is most needed and being rewarded for it.

### 2. The Greed "Tail-Risk" Trap
While "Greed" days show positive average PnL, they harbor catastrophic downside risk.
> **Finding:** Euphoria leads to over-leverage. The **Risk Analysis (Cell 117)** reveals that while the mean PnL is positive, the "tail-risk" (extreme outliers) is massive. Traders are frequently wiped out by sudden reversals during euphoric blow-off tops.

### 3. Efficiency: Quality Over Quantity
> **Finding:** High-frequency trading in this cohort is negatively correlated with net PnL. This is largely due to fee erosion (peaking at >$4/trade) and "churning" in sideways markets. Selective, high-conviction trading ("Infrequent" segment) yielded a PnL of **$96.94** vs **$42.49** for frequent fliers.

---

## 💡 Actionable Output: The "Sentiment-Adjusted" Framework (Part C)

Based on the EDA, I propose the following two programmatic trading rules:

### Rule 1: The "Anti-Fragile" Fear Protocol
* **Trigger:** Fear & Greed Index < 25.
* **Strategy:** Increase **Position Size by 50%** but decrease **Trade Frequency by 30%**.
* **Rationale:** Capitalize on the higher average PnL found in Fear days while avoiding the high fee-burn associated with over-trading.

### Rule 2: The "Greed-Tail" Kill Switch
* **Trigger:** Fear & Greed Index > 75.
* **Strategy:** Implement a **Hard Leverage Cap (Max 3x)** and a daily loss limit of 1% of equity.
* **Rationale:** Specifically targets the massive drawdown outliers (-$350k+) identified in the Greed sentiment segment to preserve capital during market extremes.

---

## 💻 Tech Stack & Setup
* **Languages:** Python 3.x
* **Libraries:** `pandas`, `matplotlib`, `seaborn`, `numpy`, `scipy`
* **Environment:** Jupyter Notebook / Google Colab

### How to Run
1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas matplotlib seaborn numpy scipy
    ```
3.  **Run Analysis:**
    Open `analysis.ipynb` and run all cells to reproduce the statistical tests and visualizations.

---

## 🏁 Conclusion
The data suggests that **Sentiment is a volatility multiplier.** Successful traders on Hyperliquid are those who provide liquidity during Fear (high size, low frequency) and strictly manage their downside during Greed.

**Author:** [Your Name]  
**Contact:** [Your Email/LinkedIn]  
**Role:** Data Science / Analytics Intern Candidate
