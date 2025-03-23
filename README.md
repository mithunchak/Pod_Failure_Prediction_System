# GuidewireHackathon
# Pod Failure Prediction System

This project monitors Kubernetes pods, collects metrics using Prometheus and the Kubernetes API, performs feature engineering, and trains a neural network model to predict pod failures. The system generates a reusable `model.h5` file for predicting the likelihood of any failure across pods.

## Overview

The system consists of three main components:
1. **Data Collection**: Fetches real-time pod metrics (CPU, memory, network, etc.) and status from a Kubernetes cluster and Prometheus, saving them to `pod_metrics.csv`.
2. **Feature Engineering**: Cleans and transforms the dataset, creating binary failure labels and scaling features, resulting in `transformed_dataset.csv`.
3. **Model Training**: Trains a Keras neural network to predict a generalized "Any_Failure" outcome, saving the model as `model.h5` and the scaler as `scaler.pkl`.

## Dataset

- **Source**: Generated from a Kubernetes cluster in the `otel-demo` namespace using Prometheus (`http://127.0.0.1:36007`) and the Kubernetes API.
- **Output**: `pod_metrics.csv` (raw data), `transformed_dataset.csv` (engineered features).
- **Features**: Includes CPU/memory usage, network metrics, pod status, event details, and more.
- **Target**: `Any_Failure` (1 if any failure type occurs, 0 otherwise).

## Requirements

- Python 3.8+
- Libraries:
  - `requests`, `pandas`, `numpy`, `scikit-learn`, `tensorflow`, `kubernetes`, `python-dateutil`
  - Install with: `pip install -r requirements.txt`
- Kubernetes cluster access with `kubectl` configured.
- Prometheus instance running at `http://127.0.0.1:36007` (adjust `PROMETHEUS_URL` if different).

## Setup

1. **Clone the Repository**:
   bash
   git clone <repository-url>
   cd pod-failure-prediction```
