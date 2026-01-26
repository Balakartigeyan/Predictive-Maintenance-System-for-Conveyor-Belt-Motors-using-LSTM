# AI-Powered Predictive Maintenance for Conveyor Belt Motors

[![Status](https://img.shields.io/badge/status-proof%20of%20concept-blue.svg)](https://github.com/)
[![Python](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](LICENSE)

## Project Overview

This repository contains an end-to-end Machine Learning solution for predictive maintenance of conveyor belt motors in heavy-industry environments (e.g., mining, manufacturing). It simulates realistic sensor telemetry (temperature, vibration, load, speed, current) and demonstrates model development, anomaly detection, forecasting, and explainability workflows that operations teams can use to detect faults before failures occur and reduce unplanned downtime.

Key capabilities:
- Predict impending motor failures (classification)
- Detect anomalous behavior (unsupervised anomaly detection)
- Forecast time-series trends for proactive maintenance planning
- Provide explainable model outputs to support operational decision-making

## Objectives

- Predict motor failures before they occur
- Detect abnormal or degrading behavior using anomaly detection
- Reduce unplanned downtime and maintenance costs
- Provide explainable AI insights for operations teams and maintenance engineers

## Use Cases

Designed for:
- Mining conveyor belt motors
- Heavy industrial equipment
- Manufacturing production lines

Business impact:
- Early fault detection and alerting
- Improved equipment reliability
- Data-driven maintenance scheduling and cost reduction

## Machine Learning Approach

Models implemented in this project:
- Random Forest — baseline failure prediction
- XGBoost — higher-accuracy classification model
- LSTM — time-series forecasting for sensor trends
- Isolation Forest and Autoencoder — anomaly detection

Primary features used:
- Motor temperature
- Vibration levels
- Motor load
- Shaft speed (RPM)
- Electrical current
- Ambient temperature

Typical pipeline stages:
1. Data ingestion and simulation
2. Exploratory data analysis and feature engineering
3. Supervised training (classification)
4. Time-series forecasting
5. Anomaly detection and alerting
6. Explainability and model monitoring

## Project Structure

.
├── data/  
│   └── sensor_data.csv  
├── notebooks/  
│   └── predictive_maintenance.ipynb  
├── models/  
│   └── trained_model.pkl  
├── outputs/  
│   ├── predictions.csv  
│   └── plots/  
├── README.md  
├── requirements.txt  
└── LICENSE

## Quickstart

Prerequisites
- Python 3.9+
- pip

1. Create and activate a virtual environment (recommended)
```bash
python -m venv .venv
source .venv/bin/activate   # macOS / Linux
.venv\Scripts\activate      # Windows (PowerShell)
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Explore the analysis and run experiments
- Open the primary notebook:
```bash
jupyter lab notebooks/predictive_maintenance.ipynb
```

4. Run scripts (example)
- Train a model (if training scripts are provided):
```bash
python scripts/train.py --data data/sensor_data.csv --output models/trained_model.pkl
```

- Run inference:
```bash
python scripts/infer.py --model models/trained_model.pkl --input data/sensor_data.csv --output outputs/predictions.csv
```

(Replace script names and arguments as appropriate if scripts differ in this repo.)

## Data

- data/sensor_data.csv: Simulated sensor telemetry including timestamps and the features listed above. Each row corresponds to a time-slice for a motor instance.
- For production, replace simulation data with a secure ingestion pipeline such as MQTT/Kafka, or from your historian/SCADA system.

Data governance notes:
- Ensure time synchronization and consistent sampling rates across sensors.
- Labeling strategy: use maintenance logs and failure events to create supervised labels; consider synthetic augmentation where needed.

## Model Evaluation

Suggested metrics:
- Classification: Precision, Recall, F1-score, ROC-AUC (emphasize recall for safety-critical detection)
- Forecasting: MAE, RMSE, MAPE
- Anomaly Detection: Precision@k, ROC-AUC (if labeled anomalies exist)

Include cross-validation, class imbalance handling (resampling, class weights), and temporal validation for time-series models.

## Explainability

Recommended tools and approaches:
- SHAP for feature attribution on tree-based models (Random Forest, XGBoost)
- Integrated gradients or attention visualizations for deep models
- Global and local explanations to support operations decisions and root-cause analysis

## Deployment & Monitoring Recommendations

Deployment options:
- Containerize models and expose an inference API (FastAPI / Flask) behind an autoscaled service
- Streaming/edge inference: deploy lightweight models on edge devices using ONNX or TensorFlow Lite
- Batch inference for predictive maintenance scheduling

Monitoring:
- Monitor input data drift and model performance (label latency)
- Set alert thresholds and integrate with Ops tools (PagerDuty, Slack)
- Log predictions, features, and explanations for audits and model retraining

## Outputs

- outputs/predictions.csv: Model prediction results and timestamps
- outputs/plots/: Visual diagnostics, model performance charts, and forecast plots

## Contributing

Contributions are welcome. Suggested workflow:
1. Fork the repository
2. Create a feature branch: `git checkout -b feat/<your-feature>`
3. Run tests and add new tests where applicable
4. Open a Pull Request describing the changes and rationale

Please follow standard best practices:
- Add unit/integration tests for scripts
- Keep changes focused and well-documented
- Include reproducible examples in the notebooks

## Roadmap / Next Steps

- Add streaming ingestion examples (Kafka / MQTT)
- Add CI for model training and validation
- Improve synthetic data realism or provide connectors for real telemetry sources
- Add automated retraining and model registry integration (e.g., MLflow)

## License

This project is provided under the MIT License. See LICENSE for details.

## Contact

Maintainer: Balakartigeyan  
GitHub: https://github.com/Balakartigeyan

Acknowledgements:
- Open-source ML libraries (scikit-learn, XGBoost, PyTorch / TensorFlow)
- Industrial data domain experts for requirements and validation
