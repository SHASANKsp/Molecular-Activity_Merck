# Molecular Activity Prediction from Chemical Descriptors
To develop safe and effective medicines by predicting molecular activity.
## Overview
This repository contains an  framework for predicting **compound biological activity** using **structure-derived molecular descriptors only**.
The project evaluates multiple modeling strategies across **15 independent activity endpoints (ACT1–ACT15)** and compares classical ML, ensemble learning, and neural network approaches.

The core motivation is practical:
**How far can we push activity prediction using only SMILES-derived descriptors, without assay-specific biological features?**

---

## Dataset & Features
* **Input**: Molecular descriptors derived from compound SMILES. The data was downloaded from  [Kaggle-Merck Molecular Activity Challenge](https://www.kaggle.com/competitions/MerckActivity/overview), and only had features(descriptors) without anly context about the molecule.
* **Output**: Continuous activity values (a regression problem)
* **Targets**: 15 independent activity endpoints (ACT1–ACT15)
* **No biological assay metadata** is used by design
---


### File Descriptions

#### `EDA.ipynb`

* Exploratory data analysis
* Descriptor distributions
* Target variability across ACT endpoints
* Initial sanity checks (missing values, scale issues, outliers)

#### `Molecular_activity.ipynb`

* Classical machine learning workflows
* Per-ACT model training and evaluation
* Ensemble strategies for selected ACTs
* Performance comparison across endpoints

#### `NN_model.ipynb`

* Fully connected neural network regressors
* Different NN architectures evaluated per ACT
* Regularization, dropout, and optimization experiments
* Used selectively where NN outperformed classical models

#### `Merck_molecular_activity.pptx`

* High-level project summary
* Model selection per ACT endpoint
* Final modeling strategy adopted for each task
* Results overview and conclusions 

---

## Modeling Strategy

Each activity endpoint is treated as a **separate regression problem**.

### Models Used

* **Neural Networks**

  * Multi-layer fully connected regressors
* **Ensemble Models**
  * Support Vector Regressor (SVR), Kernel Ridge Regression and Gaussian Process Regressor was Combined using stacking
* **XGBoost**

There is **no single “best” model**—model choice is endpoint-dependent.

---

## Key Observations

* Descriptor-only models saturate performance quickly for some ACTs
  → Indicates label noise or missing biological context
* Ensembles consistently outperform single classical models
* Neural networks help when descriptor–activity relationships are strongly nonlinear
* Performance heterogeneity across ACTs is significant and expected
---

## Limitations
* No biological assay context
* No target-specific information
* Descriptor quality bounds model ceiling

These are **design choices**, not oversights.

---

