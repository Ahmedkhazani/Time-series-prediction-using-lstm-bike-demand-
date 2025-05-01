# Bike Sharing Demand Prediction

**Author:** Khazani Ahmed Ibrahim  
**Objective:** Predict bike-sharing demand for the next 60 minutes at each station using historical data and LSTM neural networks.

---

## 1. Introduction

Bike-sharing systems are an efficient and sustainable mode of urban transportation, but managing supply and demand remains a challenge. This project aims to predict near-term bike demand at each station using a deep learning approach to improve resource allocation and user satisfaction.

---

## 2. Dataset

The dataset contains ride-level data with the following fields:
- `ride_id`
- `rideable_type`
- `started_at`, `ended_at`
- `start_station_id`, `end_station_id`
- `start_lat`, `start_lng`, `end_lat`, `end_lng`
- `member_casual`

### Key Insights:
- Rush hours (8–10 AM and 5–7 PM) show peak demand.
- Weekday usage is higher than weekends.
- Casual riders generally have longer ride durations.
- Certain stations consistently have high demand.

---

## 3. Methodology

### Data Preprocessing
- Temporal features extracted (hour, weekday, month).
- Demand aggregated per station per hour.
- Features scaled with `MinMaxScaler`.
- 24-hour input windows created for LSTM sequences.

### Model Architecture
- **Model Type:** LSTM
- **Layers:**
  - 2 LSTM layers (64 units each)
  - Dropout layers to prevent overfitting
  - Dense layer (32 units)
  - Output layer for next-hour demand
- **Loss:** Mean Squared Error (MSE)
- **Optimizer:** Adam (lr=0.001)
- **Metric:** Mean Absolute Error (MAE)

### Training Parameters
- Epochs: 50
- Batch size: 32
- Early stopping enabled

---

## 4. Results

- **Test Loss:** 0.0008  
- **Test MAE:** 0.0201  

The LSTM model demonstrates strong performance in capturing temporal demand patterns with low error.

---

## 5. Discussion

### Key Findings
- Accurate temporal pattern prediction
- Feature scaling and sequence creation enhanced performance
- High-variability stations may benefit from additional data (e.g., weather)

### Limitations
- No weather or event data included
- Some stations may need separate models

---

## 6. Conclusion

The LSTM-based model effectively predicts hourly bike-sharing demand. Future work may involve:
- Integrating weather and event data
- Real-time deployment
- Experimenting with Transformer-based models
