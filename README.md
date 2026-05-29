# ☀️ Solar Irradiance Prediction

Predicting solar radiation levels using meteorological data from the HI-SEAS weather station, employing feature engineering, XGBoost, and a Multilayer Perceptron (MLP) neural network.

---

## 📋 Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Models & Results](#models--results)
- [Tech Stack](#tech-stack)
- [How to Run](#how-to-run)

---

## 📌 Overview

Solar irradiance prediction is critical for optimizing solar energy systems and planning renewable energy output. This project builds regression models to predict solar radiation (W/m²) using weather features like temperature, humidity, wind speed, and time-based variables extracted from timestamps.

---

## 📂 Dataset

- **Source:** [HI-SEAS Weather Station Dataset — Kaggle](https://www.kaggle.com/datasets/dronio/SolarEnergy)
- **Period:** September – December 2016 (Missions IV & V)
- **Size:** 32,686 records × 14 engineered features

**Key features used:**
| Feature | Unit |
|---|---|
| Solar Radiation (target) | W/m² |
| Temperature | °F |
| Humidity | % |
| Barometric Pressure | Hg |
| Wind Speed | mph |
| Wind Direction | Degrees |
| Sunrise / Sunset Time | Hawaii time |

---

## 🔄 Project Workflow

1. **Data Loading & Exploration** — initial inspection, shape and null value checks
2. **Data Wrangling** — extracted Month, Day, Hour, Minute, Second from datetime; parsed sunrise/sunset times using regex; dropped raw timestamp columns
3. **Feature Selection** — three methods applied:
   - Pearson Correlation Matrix (heatmap)
   - SelectKBest (Chi-squared test)
   - ExtraTreesClassifier feature importances
4. **Feature Engineering** — applied optimal transformations per feature:
   - Log transform → Temperature, Wind Speed
   - Box-Cox transform → Pressure, Humidity
   - Min-Max scaling → Wind Direction
5. **Data Preparation** — 80/20 train-test split, StandardScaler normalization (14 features, 26,148 training samples)
6. **Modelling** — XGBoost Regressor and MLP Neural Network

---

## 📊 Models & Results

### XGBoost Regressor
| Metric | Score |
|---|---|
| RMSE | 81.44 |
| R² Score | **0.93** |

> Parameters: `learning_rate=0.1`, `max_depth=8`

### Multilayer Perceptron (Keras)
Architecture: `Dense(128) → Dropout(0.33) → Dense(64) → Dropout(0.33) → Dense(32) → Dropout(0.33) → Dense(1)`

| Metric | Score |
|---|---|
| MAE | 40.68 |
| MSE | 9589.30 |

> Optimizer: Adam (lr=0.001) | Loss: MAE | Epochs: 50 | Batch size: 32

**XGBoost achieved R² = 0.93**, explaining 93% of the variance in solar radiation — strong predictive performance on unseen data.

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat)

---

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/pawanahirwa/Solar-Irradiation-Prediction.git
   cd Solar-Irradiation-Prediction
   ```

2. **Install dependencies**
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn xgboost tensorflow scipy
   ```

3. **Download the dataset** from [Kaggle](https://www.kaggle.com/datasets/dronio/SolarEnergy) and place `solar_irradiance data.csv` in the project root.

4. **Run the notebook**
   ```bash
   jupyter notebook "Solar Irradiance Prediction.ipynb"
   ```

---

## 👤 Author

**Pawan Singh Ahirwar**
- GitHub: [@pawanahirwa](https://github.com/pawanahirwa)
- Affiliation: IRCC, IIT Bombay# Solar-Irradiation-Prediction
Solar Irradiation Prediction
