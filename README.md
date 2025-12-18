## Detecting Financial Market Regimes
### Project Overview
This project investigates the use of unsupervised learning methods to detect financial market regimes—periods of similar market behavior using historical S&P 500 time-series data. The focus is on understanding how feature engineering and clustering model choice affect regime interpretability and temporal consistency, rather than on price prediction or trading performance.

The work compares multiple clustering techniques across different feature sets to evaluate their suitability for historical market analysis and as inputs to downstream financial models.

### Key Results
![img](https://github.com/nandhika03/Detecting_Financial_Market_Regimes/blob/main/Reports/HMMRegimesover6month.png)
- Hidden Markov Models produced the most interpretable regimes when applied to simple, smoothed feature sets, exhibiting temporal persistence and coherent transitions. 
- K-Means and Fuzzy C-Means performed better on multivariate feature sets, producing simpler and more visually interpretable clusters, though sometimes at the cost of oversimplification.
- Gaussian Mixture Models consistently produced low-confidence and visually ambiguous regime assignments.
- Objective clustering metrics did not always align with human interpretability, highlighting a trade-off between quantitative evaluation and practical usefulness.
![img](https://github.com/nandhika03/Detecting_Financial_Market_Regimes/blob/main/Reports/Comparison%20of%20Regime%20Assignments%20Across%20Clustering%20Models%20(K-Means%2C%20FCM%2C%20HMM).png)
---


- The[ code directory ](https://github.com/nandhika03/Detecting_Financial_Market_Regimes/tree/main/Code)contains all experiments implemented in Python using Google Colab.
- The[ report directory ](https://github.com/nandhika03/Detecting_Financial_Market_Regimes/tree/main/Reports)contains the final report and all supporting figures.

---

### Data Description
- **Dataset:** S&P 500 Index (`^GSPC`)
- **Source:** Yahoo Finance
- **Time period:** January 1, 1990 – January 1, 2024
- **Frequency:** Daily data, resampled to monthly where appropriate
- **Base variables:** Open, High, Low, Close, Volume

---

### Feature Engineering
Multiple feature sets were engineered to capture market behavior at different time scales.

#### Engineered Features
- Daily returns  
- 10-day return momentum  
- 10-day rolling volatility  
- Monthly returns  
- Cumulative monthly returns  
- Monthly rolling volatility  
- 6-month moving average of cumulative returns  
- 6-month moving average of volatility  
- 3-month percent change in monthly closing price  
- 12-month rolling z-score of monthly returns  

#### Feature Set Configurations
1. **Univariate smoothed feature set** (long-term trends)
2. **Multivariate smoothed feature set** (reduced-noise long-term patterns)
3. **Multivariate high-frequency feature set** (short-to-medium-term dynamics)

---

### Models Evaluated
The following unsupervised learning models were implemented and compared:

- K-Means Clustering  
- Fuzzy C-Means (FCM)  
- Hidden Markov Model (HMM)  
- Gaussian Mixture Model (GMM)  

The number of regimes was selected through hyperparameter tuning using clustering-specific metrics such as silhouette score, fuzzy partition coefficient (FPC), and log-likelihood.

---

### Real-World Applicability
This project demonstrates the feasibility of identifying and interpreting market regimes in historical financial data.

Potential applications include:
- Historical market regime visualization
- Strategy conditioning based on regime context
- Risk-aware market analysis (e.g., identifying high-volatility or transition periods)
- Use of regimes as inputs to downstream forecasting or trading models

This work does **not** evaluate trading performance, predictive accuracy, or financial returns.

---

### Limitations
- Fixed historical time window (1990–2024) with no rolling or adaptive retraining
- No out-of-sample or forward validation
- Regime interpretation is subjective and model-dependent
- Results may not generalize to other assets or markets
- No evaluation using financial performance metrics (e.g., returns, drawdowns, Sharpe ratio)

---

### Technologies Used
- Python  
- Google Colab  
- NumPy, Pandas  
- scikit-learn  
- hmmlearn  
- matplotlib, seaborn 
---

### Future Work
- Rolling-window or adaptive regime detection
- Out-of-sample regime stability analysis
- Regime-conditioned forecasting models
- Extension to individual equities or sector-level data
- Integration with portfolio risk metrics

---

### Authors
- **Blake Krouth** – Data acquisition, EDA, literature review, univariate analysis  
- **Ganesh Vannam** – K-Means and GMM modeling, visualization, temporal consistency testing  
- **Nandhika Rajmanikandan** – Feature engineering, Fuzzy C-Means and HMM implementation, exploratory extensions
