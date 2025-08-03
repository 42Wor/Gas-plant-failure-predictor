# Gas Plant Predictive Maintenance Model

This project demonstrates the development and evaluation of a predictive maintenance model using a Long Short-Term Memory (LSTM) neural network. The model predicts the Remaining Useful Life (RUL) of critical assets to anticipate failures before they occur, enabling proactive maintenance scheduling.

While framed for a "Gas Plant" scenario, the project utilizes the **NASA Turbofan Engine Degradation Simulation Dataset** as a high-fidelity proxy for real-world industrial sensor data.

## Dataset
- **Source:** [NASA C-MAPSS Jet Engine Simulated Data](https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data)
- **Description:** Time-series data from simulated turbofan engines with:
  - 21 sensor readings per cycle
  - 3 operational settings per cycle
  - Multiple engines run to failure with varying initial wear
- **Subset Used:** `FD001` (single fault mode and operating condition)

## Model Architecture
The core predictor is an **LSTM (Long Short-Term Memory)** neural network built with TensorFlow/Keras, chosen for its ability to learn long-term dependencies in sequential sensor data.

- **Saved Model:** `gas_plant_failure_predictor.h5`
- **Advantages:**
  - Captures temporal patterns in sensor data
  - Effective for failure precursor detection
  - Persistent model for future use without retraining

## Results & Visualizations

### 1. Model Accuracy: Predicted vs. Actual RUL
![Predicted vs. Actual RUL on Test Data](https://github.com/42Wor/Gas-plant-failure-predictor/raw/main/Predicted_vs_Actual.png)

- Shows correlation between predicted and actual RUL values
- Strong positive correlation indicated by points clustering near diagonal
- Visual confirmation of model's predictive accuracy

## Fleet Health - PLT 100 Engine Dashboard

### Overview
Color-coded visualization of engine health status across the fleet for quick identification of critical units.

### Key Performance Indicators (KPIs)
| Color       | Status                      | Action                      |
|-------------|-----------------------------|-----------------------------|
| **Green**   | Normal Operation            | Continue monitoring         |
| **Orange**  | Warning - Monitor Closely   | Schedule inspection         |
| **Red**     | Critical                    | Immediate maintenance       |

![Fleet Health Dashboard](https://github.com/42Wor/Gas-plant-failure-predictor/raw/main/Fleet_Health.png)

## Actionable Reports
Complete model testing reports for all 100 engines available in:

- `MAINTENANCE_DASHBOARD_PHOENIX_2463_2025-08-02.xlsx`  
- `Maintenance_Report_20250802_0234.xlsx`
