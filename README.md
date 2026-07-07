# Velora

> **Enterprise-grade real-time MLOps platform for automated data ingestion, distributed processing, machine learning, drift detection, and continuous deployment.**

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![PySpark](https://img.shields.io/badge/PySpark-Structured%20Streaming-orange?logo=apachespark)
![Apache Kafka](https://img.shields.io/badge/Apache-Kafka-black?logo=apachekafka)
![Apache Iceberg](https://img.shields.io/badge/Apache-Iceberg-0F62FE)
![MLflow](https://img.shields.io/badge/MLflow-MLOps-0194E2)
![FastAPI](https://img.shields.io/badge/FastAPI-REST_API-009688?logo=fastapi)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestrated-326CE5?logo=kubernetes)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI/CD-2088FF?logo=githubactions)
![License](https://img.shields.io/badge/License-MIT-green)

---

# Overview

**Velora** is a production-inspired Machine Learning platform that demonstrates how modern organizations build, deploy, and maintain intelligent systems at scale.

Unlike traditional machine learning projects that stop after training a model, Velora showcases the complete machine learning lifecycle—from real-time data ingestion to automated deployment and continuous monitoring.

The platform simulates an e-commerce environment where streaming transaction data is processed through a modern Big Data ecosystem. Incoming data is transformed into features, stored in a Lakehouse architecture, used to train machine learning models, monitored for drift, and automatically retrained whenever production data changes significantly.

Velora is designed to resemble the architecture used by companies such as Amazon, Netflix, Uber, Grab, and Airbnb.

---

# Features

- Real-time event streaming using Apache Kafka
- Distributed data processing with PySpark Structured Streaming
- Apache Iceberg Lakehouse storage
- Automated feature engineering
- Feature Store
- Machine Learning training pipeline
- MLflow experiment tracking & model registry
- Automated data drift detection
- Continuous model retraining
- FastAPI inference service
- Docker containerization
- Kubernetes deployment
- Prometheus & Grafana monitoring
- GitHub Actions CI/CD
- Automated testing

---

# Objectives

Velora demonstrates production-ready engineering skills across:

- Data Engineering
- Machine Learning Engineering
- MLOps
- Software Engineering
- Distributed Computing
- Cloud-Native Development
- CI/CD Automation

---

# System Architecture

```text
                   Customer Events
                          │
                          ▼
                Event Generator (Python)
                          │
                          ▼
                    Apache Kafka
                          │
                          ▼
             PySpark Structured Streaming
                          │
                          ▼
                  Apache Iceberg Lakehouse
                          │
                          ▼
                 Feature Engineering Layer
                          │
                          ▼
                     Feature Store
                          │
                          ▼
               ML Training Pipeline
                          │
                          ▼
                  MLflow Model Registry
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
       Drift Detection          Model Evaluation
              │
              ▼
      Automatic Retraining
              │
              ▼
          FastAPI REST API
              │
              ▼
        Docker + Kubernetes
              │
              ▼
 Prometheus + Grafana Monitoring
```

---

# Automated Retraining Pipeline

Whenever production data drifts away from the original training data, Velora automatically launches a retraining workflow.

```text
Incoming Data
      │
      ▼
Drift Detection
      │
      ▼
Threshold Exceeded?
      │
 ┌────┴─────┐
 │          │
No         Yes
 │          │
 ▼          ▼
Continue  Retrain Model
              │
              ▼
      Evaluate Performance
              │
              ▼
 Deploy New Model Automatically
```

No manual intervention is required.

---

# Tech Stack

| Category | Technology |
|------------|------------|
| Programming Language | Python |
| Streaming | Apache Kafka |
| Distributed Processing | PySpark Structured Streaming |
| Lakehouse | Apache Iceberg |
| Storage Format | Parquet |
| Workflow Orchestration | Apache Airflow |
| Feature Store | Feast *(planned)* |
| Machine Learning | Scikit-learn |
| Gradient Boosting | XGBoost, LightGBM, CatBoost |
| Experiment Tracking | MLflow |
| Drift Detection | Evidently AI |
| API | FastAPI |
| Containerization | Docker |
| Orchestration | Kubernetes |
| Monitoring | Prometheus |
| Visualization | Grafana |
| CI/CD | GitHub Actions |
| Testing | Pytest |
| Code Quality | Ruff, Black |

---

# Project Structure

```text
velora/

├── configs/
│
├── ingestion/
│   ├── kafka_producer.py
│   ├── kafka_consumer.py
│
├── streaming/
│   ├── spark_stream.py
│
├── iceberg/
│   ├── catalog.py
│
├── feature_store/
│   ├── feature_engineering.py
│
├── training/
│   ├── train.py
│   ├── evaluate.py
│   ├── retrain.py
│
├── inference/
│   ├── app.py
│
├── monitoring/
│   ├── drift.py
│   ├── metrics.py
│
├── airflow/
│   └── dags/
│
├── docker/
│
├── kubernetes/
│
├── dashboards/
│
├── notebooks/
│
├── tests/
│
├── docs/
│
├── requirements.txt
│
└── README.md
```

---

# Data Flow

### 1. Event Generation

A Python service continuously simulates:

- Customer purchases
- Product inventory
- Competitor prices
- Seasonal demand
- Promotions
- Holidays
- Weather

↓

### 2. Streaming

Events are published into **Apache Kafka**.

↓

### 3. Distributed Processing

**PySpark Structured Streaming** processes incoming events in real time.

Tasks include:

- Cleaning
- Validation
- Window Aggregation
- Feature Generation

↓

### 4. Lakehouse Storage

Processed data is stored in **Apache Iceberg**, providing:

- ACID Transactions
- Time Travel
- Schema Evolution
- Partition Evolution
- Snapshot Versioning

↓

### 5. Feature Engineering

Features are generated and stored in the Feature Store.

↓

### 6. Model Training

The ML pipeline automatically trains and evaluates multiple models.

Examples:

- XGBoost
- LightGBM
- CatBoost
- Random Forest

↓

### 7. MLflow

Every experiment is logged, versioned, and registered.

↓

### 8. Drift Detection

Incoming production data is continuously monitored.

If drift exceeds a threshold, Velora automatically launches a retraining pipeline.

↓

### 9. Deployment

The best-performing model is deployed through a FastAPI REST service.

---

# REST API

## Predict Price

```http
POST /predict
```

Example Request

```json
{
  "inventory": 150,
  "competitor_price": 24.90,
  "holiday": false,
  "weather": "Sunny",
  "sales_last_hour": 63
}
```

Example Response

```json
{
  "predicted_price": 26.35
}
```

---

# Monitoring

Velora provides production monitoring using **Prometheus** and **Grafana**.

Dashboard metrics include:

- API Latency
- Request Throughput
- CPU Usage
- Memory Usage
- Data Drift Score
- Current Model Version
- Model Accuracy
- Training Duration
- Prediction Latency

---

# CI/CD Pipeline

Every commit automatically triggers:

```text
Git Push
    │
    ▼
Run Tests
    │
    ▼
Lint Code
    │
    ▼
Build Docker Image
    │
    ▼
Train Model
    │
    ▼
Evaluate Model
    │
    ▼
Register Model
    │
    ▼
Deploy
```

---


# Roadmap

- [ ] Kafka Streaming
- [ ] PySpark Structured Streaming
- [ ] Apache Iceberg Integration
- [ ] Feature Store
- [ ] Automated Feature Engineering
- [ ] ML Training Pipeline
- [ ] MLflow Integration
- [ ] Drift Detection
- [ ] Automatic Retraining
- [ ] FastAPI Deployment
- [ ] Docker
- [ ] Kubernetes
- [ ] GitHub Actions CI/CD
- [ ] Prometheus Monitoring
- [ ] Grafana Dashboard
- [ ] Cloud Deployment (AWS/GCP/Azure)

---

# Future Use Cases

Velora is designed as a reusable MLOps platform capable of supporting multiple machine learning applications.

Examples include:

- Dynamic Pricing
- Customer Churn Prediction
- Recommendation Systems
- Fraud Detection
- Credit Risk Scoring
- Demand Forecasting
- Predictive Maintenance
- Sales Forecasting

---

# Contributing

Contributions are welcome.

If you'd like to improve Velora, feel free to open an issue or submit a pull request.

---

# License

This project is licensed under the MIT License.
