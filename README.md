You got it. The issue with the GitHub link is a common one. A standard link to a file on GitHub (with `/blob/`) points to the HTML page that displays the file, not the raw file itself. To make it work in a Markdown image tag, you need to point to the raw version of the file.

Here is the corrected and updated `readme.md` file with the fixed image links.

---

# Gas Plant Predictive Maintenance Model

This project demonstrates how to build and evaluate a predictive maintenance model using a Long Short-Term Memory (LSTM) neural network. The goal is to predict the Remaining Useful Life (RUL) of critical assets to anticipate failures before they occur, enabling proactive maintenance scheduling.

While the project is framed for a "Gas Plant" scenario, it uses the publicly available **NASA Turbofan Engine Degradation Simulation Dataset** as a high-fidelity proxy for real-world industrial sensor data.

## Dataset

- **Source:** [NASA C-MAPSS Jet Engine Simulated Data](https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data)
- **Description:** The dataset consists of time-series data from a fleet of simulated turbofan engines. Each engine starts with varying degrees of initial wear and operates until failure. The data includes 21 sensor readings and 3 operational settings per cycle.
- **Usage:** We use the `FD001` subset for training and testing, which involves one fault mode and one operating condition.

## Model Architecture

The core of this predictor is an **LSTM (Long Short-Term Memory)** neural network built with TensorFlow/Keras. LSTMs are ideal for this task because they can learn long-term dependencies and patterns in sequential sensor data, which are often precursors to mechanical failure.

The trained model is saved and can be loaded for future use without retraining.
- **Saved Model File:** `gas_plant_failure_predictor.h5`

## Results & Visualizations

The model's performance is evaluated by comparing its RUL predictions against the ground truth values for the 100 engines in the test set.

### 1. Model Accuracy: Predicted vs. Actual RUL
This plot shows the correlation between the model's predictions and the actual RUL. A perfect model would have all points lying on the diagonal red line. Our model shows a strong positive correlation, indicating good predictive accuracy.

![Predicted vs. Actual RUL on Test Data](https://github.com/42Wor/Gas-plant-failure-predictor/raw/main/Predicted_vs_Actual.png)

### 2. Fleet Health Dashboard
This dashboard provides an at-a-glance overview of the predicted health of every asset in the fleet. Each bar represents an engine, and its height indicates the predicted RUL. The color-coding immediately identifies assets requiring attention.

- **Green:** Normal Operation
- **Orange:** Warning - Monitor Closely
- **Red:** Schedule Maintenance

![Fleet Health Dashboard: Predicted RUL for Each Engine](https://github.com/42Wor/Gas-plant-failure-predictor/raw/main/Fleet_Health.png)

## Actionable Reports

The ultimate goal is to generate actionable reports for maintenance teams. The script produces a prioritized CSV/Excel file that lists the assets most in need of attention at the top.

The reports are timestamped for version control, for example:
- `MAINTENANCE_DASHBOARD_PHOENIX_2463_2025-08-02.xlsx`
- `Maintenance_Report_20250802_0234.xlsx`

This report is the key output for making data-driven maintenance decisions.

## How to Run This Project

1.  **Prerequisites:** Ensure you have Python 3.x and the required libraries installed.
    ```bash
    pip install pandas numpy scikit-learn tensorflow matplotlib seaborn
    ```
2.  **Download the Code:** Clone this repository or download the main Jupyter Notebook / Python script.
3.  **Run the Notebook:** Execute the cells in the notebook (`gas_plant_failure_predictor.ipynb`) in order. The notebook will automatically:
    - Download and unzip the C-MAPSS dataset.
    - Preprocess and normalize the sensor data.
    - Build and compile the LSTM model.
    - Train the model and save it as `gas_plant_failure_predictor.h5`.
    - Evaluate the model on the test set and generate the visualizations.
    - Create and save the final, prioritized maintenance report as a CSV file.
