# Principal Component Analysis (PCA) of the EUR Swap Curve

This project applies **Principal Component Analysis (PCA)** to the **EUR interest rate swap curve** to identify the key drivers of curve movements and uncover **relative value (RV) dislocations** across maturities.

By decomposing daily swap rate changes into a small number of orthogonal factors, the analysis provides a structured way to understand curve dynamics and to assess whether individual tenors are trading rich or cheap relative to the overall curve.

---

## Overview

Interest rate swap curves are highly correlated across maturities, making it difficult to analyse movements on a tenor-by-tenor basis. PCA offers a way to reduce this complexity by expressing curve movements in terms of a few dominant factors.

In this notebook:
- The EUR swap curve is decomposed into its main components.
- The economic interpretation of each component is explored.
- PCA-implied rate changes are reconstructed.
- Residuals are analysed to highlight relative value opportunities.

The focus is on **relative pricing within the curve**, rather than on outright rate direction.

---

## Motivation

Movements in the swap curve are typically driven by common forces such as monetary policy expectations and macroeconomic conditions. As a result, most tenors move together.

PCA allows us to:
- Separate **systematic curve movements** from **idiosyncratic tenor behaviour**
- Identify which parts of the curve are behaving unusually
- Build a framework for **curve-neutral relative value analysis**

This approach is commonly used in fixed income trading and risk management.

---

## Methodology

The analysis follows these steps:

1. **Data preparation**  
   EUR swap rates across multiple maturities are collected and transformed into daily changes to focus on curve movements rather than levels.

2. **Principal Component Analysis**  
   PCA is applied to the swap rate changes to extract the main drivers of variation in the curve.

3. **Factor interpretation**  
   The first three principal components are interpreted as:
   - **Level**: parallel shifts of the curve  
   - **Slope**: relative movement between short and long maturities  
   - **Curvature**: belly versus wings dynamics

4. **Factor loadings analysis**  
   Loadings across tenors are examined to understand how each maturity responds to movements in the principal components.

5. **Principal component time series**  
   The realised value of each principal component is computed over time by projecting the original data onto the PCA factors.

6. **PCA-implied rate changes**  
   Daily swap rate changes implied by the PCA model are reconstructed using the factor loadings and component values.

7. **Residual calculation**  
   Residuals are computed as the difference between actual swap rate changes and PCA-implied changes.

8. **Relative value analysis**  
   Residuals are analysed and visualised to identify maturities that appear rich or cheap relative to the curve structure.

---

## Interpretation of Results

- The first three principal components typically explain the vast majority of variation in the EUR swap curve.
- PCA residuals represent movements that are **not explained** by level, slope, or curvature.
- Large residuals indicate **relative mispricing**, rather than directional rate views.

Positive residuals suggest a tenor is trading **rich**, while negative residuals suggest it is **cheap**, relative to the PCA-implied curve.

---

## Relative Value Framework

This project uses PCA residuals as a **diagnostic tool** for relative value analysis:

- Signals are **cross-sectional**, not directional.
- Trades are intended to be **curve-neutral**, targeting mean reversion.
- The framework helps distinguish genuine dislocations from normal curve behaviour.

The notebook provides a systematic way to **identify and analyse potential RV opportunities**.

---

## Tools and Requirements

- Python  
- pandas  
- numpy  
- scikit-learn  
- matplotlib / plotly  
- Jupyter Notebook  

---