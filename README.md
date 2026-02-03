1. Project Overview

This project investigates multivariate time series forecasting using recurrent neural networks. A baseline LSTM model is compared against an LSTM augmented with a temporal attention mechanism. The objective is to evaluate whether attention improves forecasting accuracy and interpretability for non-stationary, correlated time series.

The project focuses on model design, empirical evaluation, and analysis of learned temporal dependencies rather than maximizing raw performance.

2. Dataset Description

The dataset is synthetically generated using NumPy to ensure full control over temporal structure and correlations.

Characteristics:

Five correlated target time series

One exogenous variable

Linear trend component

Periodic seasonal component

Additive Gaussian noise

Total time steps: 1200

Sequence length used consistently: 40

All features are scaled using Min-Max normalization.

3. Model Architectures
3.1 Baseline LSTM

The baseline model consists of:

A single LSTM layer with 64 hidden units

A dense output layer predicting five target variables

This model treats all historical time steps uniformly and serves as a strong reference for comparison.

3.2 Attention-Based LSTM (Temporal Self-Attention)

The attention-based model extends the baseline by introducing a self-attention mechanism over the LSTM hidden states.

Architecture:

LSTM layer with return_sequences enabled

Self-attention applied over all temporal hidden states

Global average pooling to aggregate the attention-weighted sequence

Dense output layer

Important clarification:
The implemented attention mechanism operates as a temporal weighting mechanism over LSTM outputs rather than a full encoder-decoder sequence-to-sequence attention architecture. This design choice simplifies training while enabling interpretability, but it may limit performance gains.

4. Hyperparameter Selection Strategy

Hyperparameters were selected through empirical experimentation using validation loss trends rather than exhaustive search.

Tuned parameters include:

Sequence length

LSTM hidden units

Learning rate

Training epochs

The attention model uses a lower learning rate and longer training schedule to stabilize attention weight convergence.

No cross-validation was performed due to computational constraints.

5. Evaluation Metrics

Models are evaluated using:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

Mean Absolute Percentage Error (MAPE)

Evaluation is performed on a held-out test set comprising 20 percent of the data.

6. Results and Discussion

In this experiment, the baseline LSTM slightly outperformed the attention-based model on the test set.

This outcome suggests that:

The baseline LSTM is already sufficient for capturing dominant temporal patterns

The simplified attention mechanism may introduce additional parameters without sufficient benefit

Attention mechanisms require careful architectural design and tuning to outperform strong recurrent baselines

These findings are consistent with prior research showing that attention does not universally improve forecasting accuracy.

7. Attention Weight Analysis

The learned attention weights were visualized to analyze temporal importance.

Observations:

Higher weights are assigned to recent time steps

Periodic peaks align with seasonal transitions

Earlier historical points receive lower influence

This indicates that the model prioritizes recent observations while still leveraging seasonal context.

The analysis confirms that the attention mechanism learns meaningful temporal structure, even when predictive performance does not improve.

8. Limitations

The attention mechanism is not a full encoder-decoder architecture

No multi-head attention is used

No cross-validation was performed

Synthetic data may not reflect real-world noise complexity

These limitations provide direction for future work.

9. Future Work

Encoder-decoder attention models

Transformer-based forecasting architectures

Multi-step forecasting

Real-world datasets with external regressors
