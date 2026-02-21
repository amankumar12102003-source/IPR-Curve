# Reservoir Inflow Performance Relationship (IPR) Analysis



## Overview
This repository contains data models and comparative analyses for evaluating the **Inflow Performance Relationship (IPR)** of oil reservoirs. The project focuses on predicting well deliverability and forecasting future reservoir performance under various flow conditions and pressure depletions. 

It features a comprehensive evaluation of established empirical models against real-world multi-rate test data, ultimately introducing and validating a **New Correlation** for improved accuracy.

## Project Objectives
* Generate IPR curves for both saturated and undersaturated reservoirs.
* Predict future well deliverability as average reservoir pressure ($P_r$) declines.
* Compare standard industry models against historical field data.
* Perform error analysis to determine the most accurate forecasting correlation.

## Methodologies & Models Implemented

The analysis utilizes the following reservoir engineering models:

### 1. Constant Productivity Index (J) Approach
Used primarily for undersaturated reservoirs where the bottom-hole flowing pressure remains above the bubble-point pressure ($P_{wf} \ge P_b$). It assumes a linear relationship:

$$Q_o = J(P_r - P_{wf})$$

### 2. Vogel's Method
Accounts for two-phase flow in saturated reservoirs (where $P_{wf} < P_b$). It uses Vogel’s dimensionless reference curve to calculate Absolute Open Flow (AOF) and generate the IPR curve:

$$\frac{Q_o}{(Q_o)_{max}} = 1 - 0.2\left(\frac{P_{wf}}{P_r}\right) - 0.8\left(\frac{P_{wf}}{P_r}\right)^2$$

### 3. Fetkovich's Model
An analytical approach that derives flow coefficients ($C$ and $n$) directly from multi-rate flow tests to model current and future performance:

$$Q_o = C(P_r^2 - P_{wf}^2)^n$$

### 4. New Correlation
A proposed analytical correlation benchmarked against Vogel and Fetkovich models using field test data to minimize absolute prediction errors.

## Repository Structure & Data

The dataset is divided into four main calculation modules (provided as CSV files):

* **`Sheet1.csv` (Simple IPR):** Calculates the Productivity Index ($J$) and AOF for a highly undersaturated reservoir, plotting baseline $P_{wf}$ vs. $Q_o$.
* **`Sheet2.csv` (Vogel’s Analysis):** Contains calculations for saturated and undersaturated states using Vogel's equation, including future IPR predictions.
* **`Sheet3.csv` (Fetkovich’s Analysis):** Uses multi-rate test data to calculate the exponent $n$ and performance coefficient $C$. Includes future IPR forecasts assuming a constant $n$ value.
* **`Sheet4.csv` (Field Case & Validation):** Utilizes historical data from **Field Case 3: Well B, Keokuk Pool, Seminole County, Oklahoma (August 1935)**. Compares the models against initial test data ($P_r$ = 1714 psi) and a subsequent test 8 months later ($P_r$ = 1605 psi).

## Key Findings & Error Analysis

The models were validated against the Keokuk Pool field data, comparing theoretical flow rates against actual measured rates.

**Current IPR Prediction Average Absolute Errors:**
* New Correlation: **14.45%**
* Fetkovich's Method: **14.64%**
* Vogel's Method: **15.03%**

**Future IPR Prediction Average Absolute Errors (After 8 Months):**
* New Correlation: **3.47%**
* Vogel's Method: **7.05%**
* Fetkovich's Method: **11.18%**

**Conclusion:** The tested "New correlation" significantly outperforms standard industry models in predicting future well deliverability as the reservoir depletes, reducing the future prediction error to under **3.5%**.

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/IPR-Analysis.git](https://github.com/yourusername/IPR-Analysis.git)
