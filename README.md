# 📈 Quantitative Alpha Discovery: Retail Behavior on Hyperliquid

**A Data Science & Quantitative Research Assignment for Primetrade.ai** **Prepared by:** Priyanshu Upadhyay

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Wrangling-150458.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E.svg)
![Status](https://img.shields.io/badge/Status-Complete-success.svg)

---

## 📑 Executive Write-Up: Methodology, Insights, & Strategy

### 1. Methodology
This research isolates and maps predictable inefficiencies in retail trading behavior on the Hyperliquid Perpetual Futures exchange by cross-referencing high-fidelity execution records with macroscopic market sentiment indicators.
* **Data Wrangling & Dimensionality Mitigation:** Handled a highly skewed, power-law distribution among 240+ crypto assets. Implemented a robust Top-N categorical aggregation strategy, preserving distinct data structures for high-volume drivers while condensing long-tail altcoin data into a statistically significant baseline control group ("Other Altcoins").
* **Exploratory Data Analysis (EDA):** Developed a unified continuous and categorical framework to evaluate behavior across changing market regimes. Analyzed the explicit strategic intent of trades by pairing directional states against realized Profit & Loss (PnL).
* **Predictive Modeling Engine:** Built a time-series classification pipeline to forecast next-day individual account profitability. Aggregated daily trader states and applied a strict predictive lag (`t+1` target shift) to eradicate target leakage. Trained a calibrated Random Forest Classifier to map behavioral momentum against systemic market sentiment.

### 2. Key Quantitative Insights
* **The "Greed Trap" and Tail Risk Amplification:** Performance profiling reveals that while average win rates stay highly uniform across sentiment cycles (~50%), severe tail risk (maximum single-trade loss) spikes exponentially during periods of "Extreme Greed." Retail participants fail to manage risk under euphoric conditions, capturing small wins but sustaining catastrophic losses when the market reverses.
* **The Execution Premium (Market Microstructure):** Microstructure analysis highlights a severe profitability tax on aggressive execution. Traders executing Market Orders (`Crossed = True`) show heavily degraded win rates during volatile sentiment extremes compared to patient actors deploying Limit Orders (`Crossed = False`). This exposes high retail susceptibility to spread decay and slip costs during emotional market panics.
* **The Retail Over-Trading Bias:** Segmenting individual accounts by trading frequency reveals a distinct behavioral divide. Hyper-active retail accounts cluster heavily below the 50% breakeven threshold, suffering from churn and execution drag. Conversely, lower-frequency, high-capital accounts ("Whales") exhibit selective placement, resulting in vastly superior net PnL stability.

### 3. Strategy Recommendations (Rules of Thumb)
* **Strategy Rule 1 (The Anti-FOMO Execution Protocol):** During market regimes classified as "Extreme Greed," systematically restrict the use of Market Orders for entry configurations. Enforce exclusive Limit Order execution across portfolio models and scale back standard sizing metrics by 25% to protect capital against sudden liquidation wicks.
* **Strategy Rule 2 (Contrarian Capital Accumulation):** When the global market enters "Extreme Fear" states, reduce directional trade frequency by 50% across standard models to avoid high-volatility chop. Simultaneously, deploy a mean-reverting limit structure to scale into long positions when the platform's aggregate Long/Short ratio falls below 1.0, capturing cheap liquidity discarded by panicking retail accounts.

---

## 📊 Visual Analytics Highlights

The charts below showcase the core empirical relationships discovered within the Hyperliquid ecosystem.

### 1. The Contrarian Edge: Multivariate Alpha Matrix
This dashboard visualizes win rates by cross-tabulating realized closing actions against prevailing market sentiment. It highlights the structural failure of chasing long momentum during high-euphoria regimes and isolates the exact asset categories that act as a "Volatility Tax" on retail portfolios.

![Multivariate Alpha Analysis](charts/multivariate_alpha.png)  
*(Reference: Generated dynamically in Phase 2: Multivariate Analysis of the notebook).*

### 2. Performance Profiling: Win Rate vs. Sentiment
This chart demonstrates that retail win rates remain deceptively stable across changing market conditions. The true danger lies in the invisible tail risk (max drawdown) that occurs during Extreme Greed, proving that risk management, not win rate, dictates long-term survival.

![Win Rate vs Sentiment](charts/win_rate_vs_sentiment.png)  
*(Reference: Generated dynamically in Phase 2: Performance Profiling).*

### 3. The Execution Edge: Advanced Microstructure
This grouped distribution explicitly displays the performance variance between Maker and Taker actions. Patient liquidity provision (Limit Orders) maintains a clear structural edge over aggressive order crossing (Market Orders) across volatile sentiment regimes.

![Market vs Limit Order Execution](charts/advanced_micro_tail.png)  
*(Reference: Generated dynamically in Phase 3: Microstructure and Execution Analysis).*

---

## 📂 Repository Structure

    ├── analysis.ipynb                # Master Jupyter Notebook containing the quant pipeline
    ├── data/                         # Data directory containing raw Hyperliquid logs
    └── charts/                       # Exported high-resolution visual evidence
        ├── advanced_micro_tail.png
        ├── categorical_uni.png
        ├── multivariate_alpha.png
        ├── pnl_vs_sentiment.png
        └── win_rate_vs_sentiment.png

---

## ⚙️ Setup & Execution

Follow these steps to initialize the quantitative environment and reproduce the analysis pipeline locally:

### 1. Install Required Core Libraries
Ensure a Python 3.11+ environment is active, then install the quantitative stack:

    pip install pandas numpy matplotlib seaborn scikit-learn jupyter

### 2. Prepare the Data Directory
Create a `data` folder in the project root and place your Hyperliquid execution logs inside:

    mkdir data
    # Place your transaction source files inside the newly created directory

### 3. Execute the Master Pipeline
Launch Jupyter Notebook to interact with the visualizations, performance tables, and predictive modeling architectures:

    jupyter notebook analysis.ipynb