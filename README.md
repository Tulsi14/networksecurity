# 🛡️ Network Security Phishing Detection: End-to-End MLOps Pipeline

<div align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-blue.svg" alt="Python Version">
  <img src="https://img.shields.io/badge/FastAPI-0.100+-009688.svg?logo=fastapi" alt="FastAPI">
  <img src="https://img.shields.io/badge/MongoDB-Atlas-47A248.svg?logo=mongodb" alt="MongoDB">
  <img src="https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-F7931E.svg?logo=scikit-learn" alt="Scikit-Learn">
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success.svg" alt="Status">
</div>

<br>

## 📌 Executive Summary
This project is an enterprise-grade, End-to-End Machine Learning Operations (MLOps) pipeline designed to classify and detect phishing websites based on network security protocols and structural data. Built with highly modular Object-Oriented Programming (OOP) principles, the system handles automated data ingestion from MongoDB, robust feature engineering, model training, and bulk inference via a high-performance FastAPI backend.

---

## 📐 System Architecture

### 1. High-Level MLOps Architecture
The system is divided into two primary pipelines: the **Training Pipeline** (offline learning) and the **Inference Pipeline** (real-time/batch prediction).

> **Note:** *(Replace this placeholder with your overall architecture diagram)*
<div align="center">
  <img src="docs/overall_architecture.png" alt="Overall MLOps Architecture" width="800">
</div>

### 2. Data Ingestion Flow (MongoDB Integration)
Data is dynamically fetched from a MongoDB Atlas cluster, converted into Pandas DataFrames, and split into train/test repositories while maintaining strict version control.

> **Note:** *(Replace this placeholder with your Data Ingestion diagram)*
<div align="center">
  <img src="docs/data_ingestion.png" alt="Data Ingestion Flow" width="700">
</div>

### 3. Training & Transformation Pipeline
Handles missing value imputation (KNN Imputer), feature scaling, and robust outlier handling before passing the data to the Model Trainer, which evaluates multiple algorithms to select the optimal model.

> **Note:** *(Replace this placeholder with your Pipeline diagram)*
<div align="center">
  <img src="docs/training_pipeline.png" alt="Training and Transformation" width="700">
</div>

### 4. Prediction & Inference Architecture
A FastAPI-driven service that accepts bulk CSV uploads (e.g., 2000+ records), drops target features, processes the data through the serialized preprocessor (`.pkl`), predicts outcomes, and returns a lightweight HTML preview while safely storing the complete prediction dataset locally.

> **Note:** *(Replace this placeholder with your Inference Flow diagram)*
<div align="center">
  <img src="docs/inference_flow.png" alt="Inference Architecture" width="700">
</div>

---

## 📂 Source Code Structure (`src`)

The repository is structured to ensure maximum modularity and ease of CI/CD integration.

```text
📦 network-security-mlops
 ┣ 📂 docs/                           # Architecture diagrams and assets
 ┣ 📂 final_model/                    # Serialized production models (.pkl)
 ┣ 📂 networksecurity/                # Main Source Code (src)
 ┃ ┣ 📂 components/                   # Core ML components (Ingestion, Transformation, Trainer)
 ┃ ┣ 📂 constant/                     # Environment variables and hardcoded constants
 ┃ ┣ 📂 entity/                       # Data classes for configuration and artifacts
 ┃ ┣ 📂 exception/                    # Custom Exception Handling module
 ┃ ┣ 📂 logging/                      # Custom centralized logger
 ┃ ┣ 📂 pipeline/                     # Training and Prediction Pipelines
 ┃ ┗ 📂 utils/                        # Shared utility functions (I/O operations)
 ┣ 📂 prediction_output/              # Generated batch inference CSV files
 ┣ 📂 templates/                      # Jinja2 HTML templates for the API UI
 ┣ 📜 app.py                          # FastAPI Application Entry Point
 ┣ 📜 main.py                         # Manual Pipeline Execution Script
 ┣ 📜 setup.py                        # Package building and distribution
 ┗ 📜 requirements.txt                # Project dependencies