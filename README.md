This submission includes three files: 1. jupyter notebook Python code 2. presentation PowerPoint file 3. project report
### High-Frequency Mid-Price Movement Prediction
## Overview
Following Kearns and Nevmyvaka (2013),
This project investigates whether engineered microstructure features from high-frequency limit order book (LOB) data can predict short-term equity mid-price movements. 
The classification task is binary—predicting whether the mid-price at time t+1 will rise relative to time t.

## Features
The predictive features include:

Normalized spread

Volume imbalance

Smart price

Trade pressure

Signed volume

Momentum

## Data
We use millisecond-level TAQ (Trade and Quote) data from WRDS. Data is cleaned, aligned by timestamp, and restricted to the most liquid trading window (09:30–10:30) for both March and July 2023.

## Models
Three classification models are evaluated:

Logistic Regression

Random Forest

Neural Network (Multi-layer Perceptron)

## Evaluation Metrics
Performance is assessed using:

Accuracy

AUC (ROC Curve)

Feature importance

Confusion matrices under different decision thresholds (0.5 and 0.4)

## Out-of-Sample Testing
Models trained on March data are tested on July data to evaluate generalization.

## Objective
To determine whether high-frequency microstructure features can support reliable signal detection for short-horizon stock price movement prediction.

