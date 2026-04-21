
#Trader Performance vs Market Sentiment —
Primetrade.ai Assignment
Overview
Analysis of how Bitcoin market sentiment (Fear/Greed Index) relates to trader behavior and
performance on Hyperliquid DEX. The goal is to uncover patterns that can inform smarter
trading strategies.
Period: May 2023 – May 2025
Dataset: 4,307 trades across 32 unique accounts
 Dataset Information
The analysis utilizes a dataset of 4,307 trades across 32 accounts. Due to the file size
(45MB), the dataset is hosted externally.
Download trader_analysis_with_filters.csv
Note: Please ensure the CSV file is placed in the root directory before running the Jupyter
Notebook.
 Repository Notes
The .gitignore File
This project includes a .gitignore file to keep the repository clean. It is configured to:
Exclude the Dataset: The 45MB trader_analysis_with_filters.csv is ignored to
comply with GitHub’s file size limits. Please download it from the link provided in the
Dataset Information section.
Exclude Checkpoints: It prevents temporary Jupyter Notebook checkpoints
( .ipynb_checkpoints ) from cluttering the file list.
Exclude Cache: It ignores Python __pycache__ folders.
How to Set Up
1. Clone/Download this repository.
2. Download the Dataset from the Google Drive link above.
3. Move the CSV into the same folder as the primetrade_assignment.ipynb file.
4. Run the Notebook to see the analysis and generated charts.
Setup & How to Run
Requirements
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
Run the Notebook
# Place the dataset in the same folder as the notebook
# Then launch Jupyter
jupyter notebook primetrade_assignment.ipynb
Project Structure
├── primetrade_assignment.ipynb   # Main analysis notebook
├── trader_analysis_with_filters.csv  # Dataset (download from link above)
├── README.md                     # This file
└── charts/                       # Auto-generated on notebook run
├── chart1_performance.png
├── chart2_behaviour.png
├── chart3_segments.png
├── chart4_feature_importance.png
└── chart5_archetypes.png
Methodology
Data Preparation (Part A)
Loaded merged dataset: trader data aligned with daily Bitcoin Fear/Greed sentiment
Verified: 0 missing values, 0 duplicates, 4,307 rows × 9 columns
Engineered metrics: is_win, is_long, broad_sent, sent_num, size_segment
Built per-account aggregates: total_pnl, win_rate, n_trades, avg_size, pnl_std
Created 3 segmentation axes: Frequent/Infrequent, Consistent/Inconsistent,
Small/Medium/Large
Analysis (Part B)
Analysed performance and behaviour across all 5 sentiment regimes with supporting charts
and tables.
Key Insights
# Insight Chart
1 Extreme Greed is the only regime with >50% win rate (54.7%) Chart
1
2 Fear days generate higher avg PnL ($3,011) than Greed ($1,778) — high
conviction large trades
Chart
1
3 Extreme Fear triggers contrarian Long bias (53.3%) — traders buy the dip Chart
2
4 Large-position traders earn most on Fear days ($6,673) — not on Greed
($5,575)
Chart
3
5 Frequent traders outperform Infrequent traders across all sentiment
regimes
Chart
3
6 Sentiment is the 3rd most important feature in next-day profitability
prediction
Chart
4
Strategy Recommendations (Part C)
Strategy 1: Contrarian Long on Extreme Fear (Large-Capital Traders)
Rule: When sentiment == Extreme Fear , bias toward long entries for accounts in the top
size tercile.
Evidence: Large traders earn 20% more on Fear days vs Greed. Extreme Fear days already
show 53.3% long bias among top traders.
Execution: On Extreme Fear signal — allow long entries; avoid new short positions for high
capital accounts.
Strategy 2: Frequency Up on Greed (Small/Medium) | Size Down on Greed
(Large)
Rule: Split behaviour by capital tier during Greed/Extreme Greed days.
Evidence: Extreme Greed = highest win rate (54.7%) → ideal for more frequent small
trades. Large traders underperform on Greed vs Fear.
Execution: Small/Medium: +20% trade frequency on Greed days. Large: cap new positions
at 80% of normal size.
Bonus
Predictive Model: Random Forest classifying next-day profitability — 72.5% accuracy
Trader Archetypes: K-Means clustering (k=3) reveals 3 behavioral profiles:
High-Performer — high avg size, strong total PnL, moderate trade count
Active Mid-Tier — high frequency, moderate PnL, lower avg size
Cautious / Breakeven — low frequency, near-zero or negative PnL
