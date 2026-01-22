# AI-Driven Energy Forecasting: Finland National Grid

## Project Overview
This project implements a **Long Short-Term Memory (LSTM)** neural network to predict the daily energy consumption of the Finnish national grid. By leveraging historical load data, this model provides actionable insights for grid stability and renewable energy integration.

### Key Performance Metrics:
* **Prediction Accuracy**: Achieved a Root Mean Squared Error (**RMSE**) of **365.91 MW**.
* **Relative Error**: Approximately **3.6%** relative to the mean load, demonstrating high reliability for national-level policy analytics.
* **Optimization**: Model converged successfully over **60 epochs** with consistent validation loss.

---

## Data Pipeline & Preprocessing
To transform raw sensor data into model-ready features, the following pipeline was developed:

* **Temporal Resampling**: Downsampled 52,774 hourly observations into 2,184 daily averages to focus on seasonal trends and reduce stochastic noise.
* **Feature Scaling**: Utilized `MinMaxScaler` to normalize consumption values into a $[0, 1]$ range, preventing gradient explosion during training.
* **Supervised Learning Format**: Implemented a "Sliding Window" algorithm with a **100-day look-back period** to provide the model with historical context for each prediction.



---

## Model Architecture
The system uses a deep **Stacked LSTM** architecture designed to capture complex, multi-layered patterns in energy time-series data:

1.  **Input Layer**: Processes $(100, 1)$ sequences (100 days of history).
2.  **Stacked LSTM Layers**: Three layers of 50 memory units each to extract deep temporal features.
3.  **Regularization**: Integrated **Dropout (20%)** to prevent overfitting and ensure high generalization on unseen data.
4.  **Dense Output**: A final fully-connected layer to produce the continuous MW prediction.



---

## Results & Forecasting
* **Actual vs. Predicted**: Visual evaluation confirms the model accurately tracks the high-demand winter peaks (~14,000 MW) and summer troughs.
* **30-Day Future Forecast**: Implemented a recursive forecasting loop to predict consumption into the unknown future, assisting in mid-term resource planning.



---

## Tech Stack
* **Language**: Python
* **Frameworks**: TensorFlow, Keras
* **Data Science**: Pandas, NumPy, Scikit-Learn
* **Visualization**: Matplotlib

