# Detecting Financial Market Regimes

This repository contains code and experiments for detecting financial market regimes in S&P 500 time-series data using feature engineering and unsupervised learning. The goal is to identify periods of similar market behavior (regimes) that can support analysis, visualization, and potentially downstream forecasting.

## Project Overview

We study several clustering approaches on engineered features derived from daily and monthly S&P 500 (^GSPC) data (1990–2024). The models evaluated include:

- K-Means
- Fuzzy C-Means (FCM)
- Hidden Markov Models (HMMs) with Gaussian emissions
- Gaussian Mixture Models (GMMs)

We compare simple univariate feature sets with more complex multivariate feature sets and assess both objective clustering metrics and subjective interpretability of the resulting market regimes.

## Data

- **Source:** Historical S&P 500 (^GSPC) daily data from Yahoo Finance  
- **Period:** 1990-01-01 to 2024-01-01  
- **Raw fields:** Open, High, Low, Close, Volume  

From this data we derive:

- Daily returns  
- 10-day momentum (percent change in returns)  
- 10-day rolling volatility  
- Monthly returns and cumulative monthly returns  
- Rolling monthly volatility  
- 6-month moving averages of cumulative return and volatility  
- 3-month momentum in monthly closing prices  
- 12-month rolling z-score of monthly returns  

## Feature Sets

We evaluate three main feature sets:

1. **Univariate (Baseline)**  
   - 6-month rolling average of cumulative monthly returns  

2. **Multivariate Smoothed (Long-Term Trends)**  
   - Rolling monthly volatility  
   - 3-month percent change in monthly close  
   - 12-month return z-score  

3. **Multivariate High-Frequency (Short-/Medium-Term)**  
   - Daily return  
   - 10-day rolling volatility  
   - 10-day momentum  

## Methods

For each feature set, we:

1. Perform preprocessing and feature engineering.
2. Standardize features where appropriate.
3. Fit multiple clustering models:
   - K-Means (hard clustering)
   - Fuzzy C-Means (soft clustering)
   - Hidden Markov Model (time-aware, regime-switching)
   - Gaussian Mixture Model (probabilistic clustering)
4. Tune the number of regimes using:
   - Silhouette score (K-Means)
   - Fuzzy Partition Coefficient (FPC) (FCM)
   - Log-likelihood (HMM, GMM)
5. Visualize the inferred regimes over price and feature trajectories.
