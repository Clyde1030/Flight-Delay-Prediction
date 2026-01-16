# Flight-Delay-Prediction

<p align="center">
  <img src="Images/flight_delay.png" alt="Flight%20Delay%20Prediction" width="900"/>
</p>

<p align="center">
  Check out our <a href="pdf_reports/Presentation.pdf">presentation</a> &nbsp; | &nbsp;
  Read our <a href="https://medium.com/@yushenglee/predicting-flight-delay-at-scale-dd314cb34e77">Medium article</a> &nbsp; | &nbsp;
  Read our <a href="Project%20Phase%203.ipynb">paper</a>
</p>

## Background And Overview
Unpredictable flight delays cost the U.S. economy billions of dollars annually by disrupting crew schedules, gate assignments, airline operations, and passenger itineraries. In this project, we define a delay as a flight departing more than 15 minutes after its scheduled time that is consistent with U.S. Department of Transportation (DOT) standards.

We identify a significant opportunity to use machine learning to predict departure delays before a flight reaches the gate. Early prediction enables airports, airlines, and passengers to manage expectations, reallocate resources, and respond proactively to operational disruptions.

### Key Problems Addressed

Operational uncertainty: Airports struggle to anticipate delays caused by congestion, weather, and network effects.

Reactive decision-making: Most mitigation actions occur after delays are already unfolding.

Complex delay drivers: Delays are influenced by weather, temporal patterns, airline behavior, and network structure—making them difficult to model with simple rules.

### Why This Matters

Airports & airlines can optimize gate usage, crew scheduling, and congestion mitigation.

Passengers benefit from earlier alerts, alternative routing options, and improved travel experience.

Operations teams gain decision support tools grounded in historical data and predictive signals.

### So What?

By accurately predicting departure delays ahead of time, this framework enables:

Proactive operational planning

Improved on-time performance metrics

Reduced cascading delays across the airline network

## Data Structure Overview


Using the U.S. Department of Transportation On-Time Performance dataset (2015–2019), integrated with NOAA weather data and airport metadata, we analyzed over 31 million flights and engineered more than 50 features capturing temporal patterns, congestion, weather, seasonality, operational disruptions, airline reputation, and network-based PageRank metrics.

## Executive Summary

## Insights Deep Dive

## Recommendations

## Project Abstract

Exploratory analysis revealed that delays were rare but highly variable,highlighting both class imbalance and the importance of network- and weather-informed predictors. **In Phase 1**, exploratory data analysis showed strong correlations between delay duration and factors such as poor weather visibility, precipitation, congestion at major hubs, and peak-hour departures. We framed delay prediction as a binary classification task and selected Logistic Regression as the baseline model, with Random Forest and XGBoost identified as advanced modeling approaches. We also identified potential improvements through temporal features, route-based clustering, and real-time streaming predictions for airport operations dashboards. Model evaluation focused on Precision, Recall, and F1-score.

**In Phase 2**, we performed detailed analysis on **one year of data (2015)**, consisting of 5.8 million flight records, to predict whether a departing flight would be delayed (DEP_DELAY_GROUP ≥ 1) or on-time (≤ 0). We established baseline models using a robust, multi-stage feature engineering pipeline that included data cleaning, categorical encoding, feature assembly, PCA, Lasso regularization, standardized scaling, and model training. **Logistic Regression achieved a baseline performance of 27% precision, 34% recall for the delayed class**, reflecting the impact of class imbalance. **Ensemble models significantly improved performance, with Random Forest achieving 78% precision, 70% recall, and XGBoost achieving 78% precision, 74% recall**. These results were obtained using three quarters of data for training and one quarter for testing. The primary challenge identified at this stage was scaling the pipeline to five years of data while implementing multi-fold, time-aware cross-validation and holding 2019 as a final test year.

**In Phase 3**, we expanded the analysis to **five years of flight and weather data** and incorporated airline reputation scores and airline PageRank as network-aware features, capturing both operational reliability and exposure to structurally critical routes. We engineered features across multiple domains, including time-based patterns, seasonality, graph-based network structure, airline reputation, major events, natural disasters, airport maintenance disruptions, and weather conditions. After extensive preprocessing, we trained models including XGBoost, Random Forest, and Multilayer Perceptron (MLP), using rolling cross-validation across training windows from 2015–2018 and holding 2019 as a blind test set.

Our modeling pipeline consisted of raw data cleaning, label construction, feature engineering, time-respecting train/test splitting, class imbalance handling, feature transformation, model training, hyperparameter tuning, and final evaluation. **The final optimized XGBoost model** achieved a **66% recall and 77% precision for delayed flights**, with scheduled departure time, recent route performance, and airline network centrality emerging as the most influential predictors. These results demonstrate the value of combining traditional operational features with engineered reputation and network-aware metrics. The proposed framework provides actionable insights for airports and airlines, supporting better resource allocation, congestion management, and targeted interventions to improve on-time performance.

## Conclusions
Our project focused on predicting flight delays prior to departure using large-scale historical flight, weather, and operational data, addressing a critical problem that impacts airport operations. Our hypothesis was that a machine learning pipeline enriched with custom temporal, weather, operational, reputation, and network-based features could accurately predict flight departure delays.  Among the evaluated models, an optimized XGBoost classifier achieved the best performance, reaching **66% recall and 77% precision for delayed flights on a held-out 2019 test set**, demonstrating the value of combining traditional operational features with network-aware and reputation-based metrics. These results show meaningful improvements over baseline models and provide insights for proactive resource planning. Future work includes extending the dataset to include **2020–2021 flights**, exploring stacked **ensemble models**, utilizing **feature selection based on final model** and perform deeper hyper-parameter tuning to ensure gains on unseen data.
