Advanced Multivariate Time Series Forecasting with Attention
Project Overview

This project implements an advanced deep learning framework for multivariate time series forecasting using Long Short-Term Memory (LSTM) networks enhanced with an attention mechanism. The goal is to predict future values of multiple correlated time series while capturing both long-term dependencies and temporal relevance through learned attention weights.

The study compares a baseline LSTM model against an attention-augmented LSTM model using standard forecasting metrics and provides interpretability through attention weight visualization.

Key Objectives

Programmatically generate a complex, non-stationary multivariate time series dataset

Implement a baseline LSTM forecasting model

Design an attention-based LSTM architecture for sequence-to-sequence forecasting

Evaluate models using MAE, RMSE, and MAPE

Analyze learned attention weights to interpret temporal importance

Dataset Description

The dataset is synthetically generated using NumPy and consists of:

Five correlated target time series

One exogenous variable

Components include:

Linear trend

Seasonal patterns

Gaussian noise

Total time steps: 1200

Sequence length used for modeling: 40

All features are normalized using Min-Max scaling before model training.

Model Architectures
Baseline LSTM

Single LSTM layer with 64 hidden units

Fully connected output layer predicting five target variables

Learns temporal dependencies uniformly across time steps

LSTM with Attention

LSTM layer with 96 hidden units and sequence output

Self-attention mechanism to dynamically weight historical time steps

Global average pooling to form context vectors

Dense output layer for multivariate prediction

The attention mechanism enables the model to focus on the most informative segments of the input sequence.

Hyperparameter Configuration

Key parameters were tuned empirically using validation loss trends:

Parameter	Value
Sequence length	40
LSTM units (baseline)	64
LSTM units (attention)	96
Learning rate (baseline)	0.001
Learning rate (attention)	0.0005
Batch size	32
Epochs	20–30
Evaluation Metrics

Model performance is evaluated using:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

Mean Absolute Percentage Error (MAPE)

The attention-based model consistently achieves lower error values compared to the baseline LSTM.

Attention Weight Analysis

The learned attention weights are extracted and visualized as a heatmap.
This visualization highlights which historical time steps contribute most to the final prediction, demonstrating the model’s ability to capture seasonal cycles and recent temporal dependencies.

Results Summary

The attention-augmented LSTM model outperforms the baseline LSTM across all evaluation metrics, confirming the benefit of adaptive temporal weighting in multivariate forecasting tasks.
