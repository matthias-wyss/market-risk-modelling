# Market Risk Modelling: VaR, ES, and Copulas

This project focuses on market risk measurement using **Value-at-Risk (VaR)** and **Expected Shortfall (ES)**, alongside modeling cross-asset dependence using **Copulas**. The analysis is performed on historical financial data for AAPL, META, and JPM.

## Table of Contents
* [Project Overview](#project-overview)
* [Repository Structure](#repository-structure)
* [Methodology](#methodology)
* [Models Implemented](#models-implemented)
* [Key Findings](#key-findings)
* [Usage](#usage)
* [Group Members](#group-members)

## Project Overview
The objective is to estimate and backtest market risk metrics for a portfolio consisting of three major assets (AAPL, META, JPM) over the period from January 2023 to June 2025. The project explores the effectiveness of univariate models versus multivariate copula-based approaches.

## Repository Structure
- `pdfs/Report.pdf`: The final academic report detailing methodology, results, and analysis.
- `analysis.ipynb`: Jupyter Notebook containing the full Python implementation.
- `pdfs/Instructions.pdf`: The original project brief and constraints.

## Methodology
1.  **Exploratory Data Analysis**: Analysis of empirical stylized facts, including log-returns, volatility clustering, and heavy tails (Jarque-Bera tests and QQ-plots).
2.  **Univariate Risk Modeling**: Estimation of VaR and ES at 95% and 99% confidence levels using:
    * Historical Simulation (HS).
    * Parametric models (Gaussian and Student-t).
    * Conditional models (GARCH).
    * Filtered Historical Simulation (FHS).
3.  **Dependence Modeling**: Fitting and simulating from Elliptical (Gaussian, Student-t) and Archimedean (Clayton, Gumbel, Frank) copulas to capture non-linear asset correlations.
4.  **Backtesting**: Evaluation of model performance using the **Kupiec Test** (for VaR) and the **Acerbi-Székely Test** (for ES).

## Models Implemented
* **Time Series**: AR(p) + GARCH(1,1) for volatility dynamics.
* **Copulas**: 
    * *Gaussian & Student-t*: To model symmetric dependence.
    * *Clayton*: To capture lower tail dependence (extreme losses).
    * *Gumbel*: To capture upper tail dependence.
* **Simulation**: Monte Carlo simulations based on fitted copula structures.

## Key Findings
* **Volatility Clustering**: All assets exhibited significant volatility clustering, making conditional models (GARCH/FHS) superior to simple historical or unconditional parametric models.
* **Non-Normality**: Log-returns demonstrated clear "fat tails" and skewness, leading to the rejection of the Gaussian hypothesis in all cases.
* **Copula Performance**: While copulas offer a sophisticated way to model dependence, they did not systematically outperform well-specified univariate models like **FHS** in this specific portfolio. The benefits of copulas were mostly visible at extreme confidence levels (99%).
* **Risk Drivers**: Extreme losses during the sample period were primarily driven by individual asset volatility dynamics rather than complex cross-asset dependence structures.

## Usage
The analysis is implemented in Python. 
1.  Ensure you have the required packages: `numpy`, `pandas`, `scipy`, `statsmodels`, `arch`, `copulae`, and `yfinance`.
2.  Run the `analysis.ipynb` notebook to reproduce the data fetching, model fitting, and backtesting results.

## Group Members
- William Jallot
- Matthias Wyss
- Antoine Garin

---
*Developed for the Quantitative Risk Management (FIN-417) course at EPFL, Fall 2025.*