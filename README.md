# Stock Clustering Analysis

A machine learning project that clusters S&P 500 stocks based on their daily returns using various K-means clustering approaches.

## Overview

This project analyzes 486 S&P 500 stocks using their 2015 daily return data to identify groups of stocks with similar price movement patterns. The analysis compares three different K-means based clustering methodologies against a baseline model that groups stocks by their GICS (Global Industry Classification Standard) sectors.

## Dataset

- **Stock Data**: 486 S&P 500 companies from `sp_500.csv`
- **Price Data**: Daily adjusted closing prices for 2015 from `sp_500_prices.csv`
- **Time Period**: 251 trading days in 2015
- **Features**: Daily returns calculated from price changes

## Methodology

### Baseline Model
Groups stocks directly by their GICS Sector classification (11 sectors total), achieving a weighted average Spearman correlation of 0.542.

### Clustering Approaches

1. **Vanilla K-means**: Direct K-means clustering after column-wise standardization
2. **Scaled K-means**: Standardizes each stock's returns individually, then applies K-means
3. **PCA K-means**: Combines individual stock standardization with PCA dimensionality reduction (91 components explaining 80% variance) before K-means

## Key Findings

- **Scaled K-means** and **PCA K-means** both outperform the baseline with weighted average Spearman correlations of 0.554 and 0.555 respectively
- Vanilla K-means produces highly unbalanced clusters (one cluster with 209/486 stocks)
- Scaled approaches create more balanced cluster distributions
- Despite similar correlation scores, Scaled K-means and PCA K-means produce notably different clustering results

## Results Summary

| Method | Spearman Correlation Score | Notes |
|--------|------------------|-------|
| Baseline (GICS) | 0.542 | Strong industry-based reference |
| Vanilla K-means | 0.535 | Highly unbalanced |
| Scaled K-means | 0.554 | Balanced and reasonable clusters|
| PCA K-means | 0.555 | Similar to scaled but different clusters |


## Conclusion

The analysis demonstrates that price-based clustering can outperform traditional sector-based groupings measuring by the Spearman correlation within each cluster. Scaled K-means and PCA K-means offer both improved correlation scores and balanced cluster distributions. However, despite similar correlation scores, Scaled K-means and PCA K-means produce notably different clustering results. It is thus difficult to conclude which method is superior based on correlation metrics alone. A more meaningful evaluation could involve developing cluster-based trading strategies and comparing the financial performance of portfolios constructed from each method.
