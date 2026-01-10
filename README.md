# 🏎️ F1 Race Winner Predictor (Machine Learning)

A data-driven experiment to **predict the Formula 1 race winner** using historical race telemetry, qualifying performance, weather impact, and machine learning.

This project combines **FastF1 telemetry data**, **feature engineering**, and a **Gradient Boosting model** to estimate race pace and rank drivers for an upcoming Grand Prix.

---

## 📌 Project Overview

Formula 1 race outcomes depend on multiple interacting factors:

* Qualifying performance
* Historical race pace
* Track-specific characteristics
* Weather conditions (especially rain)

This project explores whether a **supervised ML model** can leverage these factors to **predict relative race performance**, using the **Brazilian Grand Prix** as a case study.

---

## 🧠 Key Ideas

* Use **previous season race sector times** as a proxy for race pace
* Combine them with **current season qualifying performance**
* Adjust predictions using a **wet-weather performance factor**
* Train a **Gradient Boosting Regressor** to predict expected race lap time
* Rank drivers by predicted pace to infer a likely winner

---

## 🗂️ Tech Stack

### Data & Analysis

* **FastF1** – Official F1 telemetry & timing data
* **Pandas / NumPy** – Data manipulation
* **Matplotlib / Seaborn** – Visualization (optional)

### Machine Learning

* **Scikit-learn**

  * GradientBoostingRegressor
  * Train/Test Split
  * Mean Absolute Error (MAE)

---

## 📊 Data Sources

### 1️⃣ Historical Race Data (2024)

* Event: **Brazilian Grand Prix**
* Extracted:

  * Lap times
  * Sector 1 / 2 / 3 times
* Aggregated per driver:

  * Mean sector times
  * Total sector time per lap

### 2️⃣ Qualifying Data (2025)

* Brazilian GP qualifying lap times
* Driver names mapped to **FastF1 3-letter codes**

### 3️⃣ Weather Adjustment

* Introduced a **Wet Performance Factor**
* Represents relative pace loss in wet conditions
* Applied when rain probability ≥ 75%

---

## ⚙️ Feature Engineering

Final model features:

| Feature               | Description                     |
| --------------------- | ------------------------------- |
| `QualifyingTime`      | Adjusted qualifying lap time    |
| `RainProbability`     | Binary / scalar rain likelihood |
| `TotalSectorTime (s)` | Avg race sector pace (2024)     |

Target variable:

* **Mean race lap time** from 2024 race data

---

## 🤖 Model Training

* **Algorithm:** Gradient Boosting Regressor
* **Parameters:**

  * `n_estimators = 300`
  * `learning_rate = 0.05`
  * `max_depth = 5`
* **Train/Test Split:** 80 / 20

The model learns a **non-linear relationship** between qualifying pace, historical race pace, and weather conditions.

---

## 🏁 Prediction Output

### 🏆 Predicted 2025 Brazilian GP Ranking

| Rank | Driver | Predicted Lap Time (s) |
| ---- | ------ | ---------------------- |
| 1    | VER    | 87.88                  |
| 2    | OCO    | 88.23                  |
| 3    | GAS    | 88.30                  |
| 4    | RUS    | 88.48                  |
| 5    | NOR    | 88.55                  |
| …    | …      | …                      |

➡️ **Predicted Winner:** **Max Verstappen (VER)**

---

## 📈 Model Evaluation

* **Metric:** Mean Absolute Error (MAE)
* **Result:**
  **🔍 MAE = 0.08 seconds**

This indicates the model predicts average lap times with **very low absolute error**, given the limited feature set.

---

## ⚠️ Limitations & Assumptions

* Uses **single-race historical data** (Brazil GP 2024)
* Weather factor is manually estimated
* No pit strategy, safety car, or tire degradation modeling
* Assumes consistent driver/team performance year-to-year

This project is intended as a **conceptual ML experiment**, not a betting or race-engineering tool.

---

## 🚀 Future Improvements

* Incorporate:

  * Tire compound data
  * Stint-level degradation
  * Safety car probability
* Replace manual rain factor with telemetry-based wet lap analysis
* Extend to **multi-race training dataset**
* Try ranking models or probabilistic outputs

---

## 👤 Author

**Spondan Bandyopadhyay**

Machine Learning • Data Engineering • Applied AI

---
