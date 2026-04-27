# Enhancing Coastal Flood Hazard Modeling with Synthetic Event Design

## Overview

This repository provides a step-by-step workflow for generating trivariate synthetic scenarios for compound coastal flooding. The framework is applied to both reanalysis and in-situ datasets, under stationary and non-stationary assumptions, and supports two complementary approaches:
Response-based approach
Design-based approach

The methodology integrates extreme value theory, copula-based dependence modeling, and data-driven sampling techniques to generate physically consistent multivariate flood scenarios.

## Workflow

### 1. Peak Extraction (POT)
A Peak-Over-Threshold (POT) analysis is applied to each variable (referred to as the center variable).
For each identified peak, the corresponding maximum values of the other two variables are extracted for trivariate extreme events.

### 2. Marginal Distribution Modeling
The center variable is modeled using a Generalized Pareto Distribution (GPD).
The associated variables are fitted with their best-fit marginal distributions.
The Cumulative Distribution Functions (CDFs) for all three variables are derived.

### 3. Dependence Modeling & Sampling
A trivariate joint distribution is constructed using copula theory and the marginals of the variables.
Synthetic samples are generated from this joint distribution, preserving the dependence structure between variables.

### 4. Return Period Analysis (Design-Based Approach)
Due to the curse of dimensionality, direct trivariate return period estimation is challenging. Instead, bivariate return period isolines are derived from the synthetic samples.
These isolines are used to define design events in the multivariate space.

### 5. Sample Reduction via Weighted Clustering (Response-Based Approach)
To reduce the large synthetic dataset, Weighted K-means (coreset-based) clustering is applied.
A representative subset of samples is selected. Each sample is assigned a weight, to be used at the end of simulation for finding the return periods.

### 6. Time Series Reconstruction & Spatial Mapping
Each synthetic event is scaled and aligned with historical time series.
Rainfall time series are further transformed into spatially distributed fields using the nearest grid cell to the used station.
