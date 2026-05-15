# US Census Population Modeling & Forecasting

## Overview
This project implements a robust data pipeline and mathematical modeling suite to analyze and forecast over two centuries of United States Census data (1790–2020). Built in Julia, it processes historical population metrics, computes decennial growth rates, and evaluates the stability of different predictive modeling techniques.

The primary objective of this project is to contrast the predictive constraints of high-degree **Polynomial Regression** against the localized stability of **Piecewise Cubic Spline Interpolation**, demonstrating the practical implications of Runge's phenomenon in real-world data forecasting.

## Key Features
*   **Automated Data Ingestion:** Parses raw `.xlsx` Census files, standardizes column types, and dynamically cleans missing or malformed data entries (e.g., null percent changes).
*   **Data Transformation:** Normalizes absolute population counts into millions and transforms temporal data into decennial intervals for numerical stability.
*   **Algorithmic Modeling:** 
    *   Iteratively computes polynomial fits from degrees $1$ through $24$.
    *   Implements piecewise cubic splines to map exact data points without edge-case oscillation.
*   **Data Visualization:** Generates automated, multi-layered visual reports contrasting historical growth rates with mathematical curve fits.

## Mathematical Approach

### 1. Polynomial Regression
The model iterates through polynomial degrees ($d$) to fit the population data $P(t)$ as a function of decades since 1790:

$$P(t) = a_0 + a_1t + a_2t^2 + \dots + a_dt^d$$

By calculating coefficients up to $d=24$, the project actively tests the boundaries of polynomial fitting. This visualizes structural overfitting and Runge's phenomenon, where higher-degree polynomials create extreme, unrealistic oscillations at the edges of the dataset, making them unsuitable for forward forecasting.

### 2. Piecewise Cubic Spline Interpolation
To resolve the instability of high-degree polynomials, the project utilizes a cubic spline. This method guarantees a smooth, continuous curve that passes exactly through every historical data point by applying distinct cubic polynomials between each interval, ensuring a highly stable model for demographic trend analysis.

## Technologies & Libraries
*   **Language:** Julia
*   **Data Engineering:** `DataFrames.jl`, `XLSX.jl`
*   **Numerical Methods:** `Polynomials.jl`, `Interpolations.jl`
*   **Visualization:** `Plots.jl`

## Setup and Installation

1. Clone this repository:
   ```bash
   git clone [https://github.com/yourusername/census-population-modeling.git](https://github.com/yourusername/census-population-modeling.git)
