# Predicting Asteroid Diameters with Machine Learning ☄️

## Project Overview

This project presents an end-to-end machine learning workflow to predict the diameter of asteroids. Using a publicly available dataset from the NASA Jet Propulsion Laboratory (JPL), this analysis explores various orbital and observational features to build a highly accurate and interpretable regression model. The primary goal is to demonstrate a sophisticated data science approach, from initial data exploration to advanced model interpretation, for a problem with real-world significance in planetary science and defense.

---

## 📊 Project Highlights

* **Advanced EDA:** Utilized density-based visualizations (`jointplot` with hexbin) to effectively analyze relationships in a large dataset and avoid overplotting.
* **Strategic Preprocessing:** Implemented a logarithmic transformation on the skewed target variable (`diameter`) to improve model stability and performance.
* **Feature Engineering:** Created a new feature (`kepler_ratio`) based on domain knowledge (Kepler's Third Law) to capture non-linear relationships.
* **High-Performance Modeling:** Trained and evaluated multiple models, with **XGBoost** emerging as the top performer.
* **Deep Model Interpretation:** Employed **SHAP** (SHapley Additive exPlanations) to provide transparent, feature-level insights into the predictions of the best model.

---

## Dataset

The dataset used is the **NASA JPL Small-Body Database Search Engine** data, which contains observational and orbital parameters for over 126,000 asteroids.

* **Source:** NASA/JPL-Caltech
* **Features:** Include orbital elements (e.g., semi-major axis `a`, eccentricity `e`), observational metrics (e.g., albedo, number of observations `n_obs_used`), and the target variable `diameter` (in km).

---

## 🚀 Methodology

The project follows a systematic, multi-stage workflow:

1.  **Exploratory Data Analysis (EDA):**
    * A statistical summary and distribution analysis revealed a significant right-skew in the target variable.
    * A correlation heatmap identified key linear relationships, while density plots uncovered more complex, non-linear patterns.

2.  **Feature Engineering & Preprocessing:**
    * The skewed `diameter` was transformed using `np.log1p`.
    * The categorical `class` feature was one-hot encoded.
    * All numeric features were standardized using `StandardScaler`.
    * The entire preprocessing workflow was encapsulated in a `ColumnTransformer` and `Pipeline` for robustness and reproducibility.

3.  **Model Training & Evaluation:**
    * Three regression models were trained and compared:
        * Linear Regression (Baseline)
        * Random Forest Regressor
        * XGBoost Regressor
    * Models were evaluated using **Root Mean Squared Error (RMSE)** on the original, untransformed scale.

4.  **Model Interpretation:**
    * SHAP was used on the best-performing model (XGBoost) to explain its predictions.
    * Global feature importance was analyzed using summary plots, and local, single-prediction explanations were generated using force plots.

---

## Results

The XGBoost model delivered the most accurate predictions, demonstrating the effectiveness of the preprocessing strategy and the power of gradient boosting for this type of dataset.

| Model               | RMSE (km) |
| ------------------- | :-------: |
| **XGBoost** | **0.5621**|
| Random Forest       |  0.5798   |
| Linear Regression   |  0.8940   |

**Key Insights from SHAP:**
* **`albedo`** (surface reflectivity) was identified as the most impactful feature. Higher albedo consistently pushes the predicted diameter down.
* **`n_obs_used`** (number of observations) and orbital parameters like **`a`** (semi-major axis) and **`i`** (inclination) were also highly influential.

---

## Getting Started

To run this project locally, follow these steps:

### Prerequisites

Ensure you have Python 3.8+ installed. The required libraries are listed in `requirements.txt`.

### Installation

1.  Clone the repository:
    ```sh
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

2.  Install the required packages:
    ```sh
    pip install -r requirements.txt
    ```
    *(Note: You will need to create a `requirements.txt` file containing the necessary libraries.)*

### Usage

The entire analysis is contained within the **`main.ipynb`** Jupyter Notebook. Open and run the cells sequentially to reproduce the findings.

---

## Technologies Used

* Python 3
* Pandas & NumPy
* Scikit-learn
* XGBoost
* SHAP
* Matplotlib & Seaborn
* Jupyter Notebook
