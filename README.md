# MSc Thesis: Urban Mobility Analysis

This repository contains the code, generative models, and data-driven analysis developed for my Master's Thesis on human urban mobility. 

The project investigates empirical trajectory predictability (focusing on information-theoretic measures like uncorrelated and correlated entropy) and introduces constrained random walk models that integrate spatial fatigue and circadian rhythms.

## 📁 Data
* **China Data:** This folder contains the data used throughout this project. It consists on 8 .csv files, containing information about the users participating in the study and the characteristics of the check-Ins they performed during the 11 days the study lasted. It also contains a Notebook created by the authors of _A human mobility dataset collected via {LBSLab}_, where the used data was presented, and a questionnaire in .pdf that served as a User Survey for the participants in the study.
  
The dataset used in this project was collected by Zhang et al. and is publicly available at [Data in Brief (Elsevier)](https://doi.org/10.1016/j.dib.2023.108898). Raw data files are not included in this repository and should be placed in the `China Data/` folder before running the notebooks.

## Overview
* **data_china.ipynb:** Exploratory data analysis and entropy computation on the empirical dataset. Loads and merges `user.csv` and `checkIns.csv`, reconstructs individual daily trajectories (with a 4AM day boundary), and computes uncorrelated ($H_u$) and correlated ($H_c$) entropy for each user via Shannon's formalism and the Lempel-Ziv estimator respectively. Includes visualization of entropy distributions, POI category analysis, and a trajectory shuffling test to assess the statistical significance of sequentiality.
* **null_model.ipynb:** Gender analysis and statistical validation. Computes $H_u$ and $H_c$ separately for male and female users and tests whether the observed entropy gap is statistically significant via a gender-label permutation null model ($10^5$ iterations). Produces the KDE distributions and confidence interval plots presented in the thesis.
* **randomwalkers-ipynb:** Generative random walk models. Implements four mobility models of increasing complexity: a pure memoryless random walk (baseline), a spatially-constrained walk with sigmoid return probability as a function of locations visited, and union/intersection combinations incorporating a temporal (circadian) return constraint anchored at 23:00. Computes $H_u$, $H_c$ and KL-divergence for each model and compares them against the empirical entropy distributions. Includes geographic visualization of individual trajectories via Folium.

## Main libraries
* NumPy / SciPy / Pandas (Data processing and simulation)
* Seaborn / Matplotlib (Data visualization)
* Folium (Visualization of geographically localized information)
