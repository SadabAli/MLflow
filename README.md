# MLflow
# MLflow – Simple Revision Notes (Future Reference)

These notes are written in **simple English** for quick revision before interviews, projects, or real work.

---

## 1. What is MLflow?

MLflow is a tool used to **track, manage, and organize machine learning experiments**.

In simple words:

> MLflow helps you remember **what model you trained, with which settings, and how well it performed**.

---

## 2. Why MLflow is needed (Real Problem)

Without MLflow:

* You train many models
* You change parameters again and again
* You forget:

  * which model was best
  * which parameters gave good accuracy
  * which model file belongs to which run

With MLflow:

* Every training is saved
* Everything is organized
* You can compare models easily

---

## 3. Core Components of MLflow

### 3.1 Experiment

* An **experiment** is a group of runs
* Example:

  * `IRIS_data`
  * `Churn_Prediction`

Used to organize related work.

---

### 3.2 Run

* A **run** = one model training
* Every time you train a model → one run

A run contains:

* parameters
* metrics
* artifacts
* model

---

### 3.3 Parameters

Parameters are **inputs you choose before training**.

Examples:

* learning_rate
* max_depth
* epochs

Why log parameters?

> So you know **which settings produced which result**.

---

### 3.4 Metrics

Metrics are **results after training**.

Examples:

* accuracy
* loss
* f1_score

Why log metrics?

> To compare different models and pick the best one.

---

### 3.5 Artifacts

Artifacts are **files saved during a run**.

Examples:

* trained model files
* plots
* validation reports
* confusion matrix

Important:

* Validation files must be logged manually
* MLflow does NOT auto-log validation

---

### 3.6 Model Logging

Models are logged using MLflow model APIs.

* Model is saved as an artifact
* Includes:

  * model file
  * signature
  * input example

`artifact_path` = folder name where model is stored

---

### 3.7 Model Signature

Model signature tells:

* input format
* output format

Why important?

> Helps during deployment and prevents wrong inputs.

---

### 3.8 Model Registry (Basic Idea)

Model Registry is like an **approval system**.

Stages:

* None
* Staging
* Production

Used to:

* mark best model
* control which model goes to production

---

## 4. MLflow Tracking URI

Tracking URI tells MLflow **where to store runs**.

Local server example:

* `http://127.0.0.1:5000`

Important:

* Local MLflow uses **HTTP**, not HTTPS
* HTTPS requires extra SSL setup

---

## 5. MLflow Server vs Local File Tracking

### Local (beginner / learning)

* Saves data in local folders
* Easy setup
* Single user

### Server (company)

* Central MLflow server
* Artifacts stored in S3 / cloud
* Multiple users

---

## 6. MLflow with Airflow (Very Important)

### Simple rule:

* Airflow = **WHEN and ORDER**
* MLflow = **WHAT HAPPENED**

Flow:

1. Airflow runs training script
2. Training script uses MLflow
3. MLflow tracks parameters, metrics, model

Airflow does NOT track metrics.
MLflow does NOT schedule jobs.

---

## 7. Validation Before Deployment (Correct Pattern)

* Train model
* Validate model
* Log validation artifacts
* Only log model if performance is good

This logic is written by **you**, not MLflow.

---

## 8. Common Mistakes (Remember This)

* Using `https` instead of `http` for local MLflow
* Forgetting to log validation artifacts
* Logging model without checking metrics
* Confusing Airflow with MLflow
* Using wrong parameter names (artifact_path vs artifacts)

---

## 9. Interview One-Liners

* "MLflow is used to track ML experiments by logging parameters, metrics, and models."
* "Airflow orchestrates ML pipelines, while MLflow tracks experiment history."
* "Model artifacts and validation artifacts must be logged explicitly in MLflow."

---

## 10. Final Mental Model (Easy to Remember)

* MLflow = experiment notebook + history + model store
* Airflow = scheduler + pipeline manager
* Docker = environment
* AWS = storage and compute

---


