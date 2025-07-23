# 🏡 California Housing Price Prediction

## 📌 Overview

This project focuses on predicting housing prices in **California, USA**, using machine learning techniques.

- 📊 **Dataset**: Sourced from the [StatLib Repository](http://lib.stat.cmu.edu/datasets/), based on data from the **1990 California Census**.
- 🧠 **Goal**: Build a robust predictive model to estimate house prices using features such as median income, housing age, location, population, etc.
- ⚙️ **Approach**: Utilizes and compares multiple **regression models** (e.g., Linear Regression, Decision Trees, Random Forest, etc.) to achieve the best performance.


<img width="750" height="750" alt="image" src="https://github.com/user-attachments/assets/123793db-3310-45e4-8598-50602819006d" />

---

## 💾 Dataset Description

| Feature Name           | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| `longitude`            | Longitude of the block group (geographical coordinate)                      |
| `latitude`             | Latitude of the block group (geographical coordinate)                       |
| `housing_median_age`   | Median age of the houses in the block group                                 |
| `total_rooms`          | Total number of rooms in the block group                                    |
| `total_bedrooms`       | Total number of bedrooms in the block group                                 |
| `population`           | Total population of the block group                                         |
| `households`           | Total number of households in the block group                               |
| `median_income`        | Median income of households in the block group (in tens of thousands)       |
| `median_house_value`   | Median house value for the block group (**target variable**)                |
| `ocean_proximity`      | Categorical: Proximity to the ocean (`<1H OCEAN`, `INLAND`, etc.)           |

🎯 **Target**: `median_house_value` — the value to be predicted.

---

## 🧹 Data Preprocessing

To prepare the data for modeling, the following steps were applied:

### 1. Handling Missing Values
- Missing entries in `total_bedrooms` were handled by:
  - Dropping rows *(for simpler runs)*, or
  - Filling them using the **median** value *(preferred)*.

### 2. Encoding Categorical Features
- `ocean_proximity` was converted into numerical values using **One-Hot Encoding**.

### 3. Feature Scaling
- Applied **StandardScaler** to normalize features such as:
  - `housing_median_age`, `total_rooms`, `total_bedrooms`, `population`, `households`, `median_income`

### 4. Feature Engineering
- New features were derived to improve model performance:
  - `rooms_per_household = total_rooms / households`
  - `bedrooms_per_room = total_bedrooms / total_rooms`
  - `population_per_household = population / households`

### 5. Train-Test Split
- Dataset was split into:
  - **Training Set**: 80%
  - **Testing Set**: 20%
- Used `random_state` to ensure reproducibility.
  
---

## 🤖 Models Used

The following regression models were trained and evaluated using **cross-validation**:

| Model               | Status     | Reason for Selection/Exclusion                                      |
|--------------------|------------|---------------------------------------------------------------------|
| **Linear Regression** | ❌ Rejected | Underfitting — failed to capture non-linear relationships in data   |
| **Decision Tree**     | ❌ Rejected | Overfitting — high variance, poor performance on validation sets    |
| **Random Forest**     | ✅ Selected | Best performance — low error, good generalization across folds      |

✅ **Final Model**: `RandomForestRegressor` was chosen based on its superior cross-validation RMSE and ability to generalize well to unseen data.

---

## 🛠️ How to Run

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/california-housing-price-prediction.git
   cd california-housing-price-prediction

  
