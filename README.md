# Subscription Conversion Prediction 📈

An end-to-end machine learning project that predicts whether a free user will convert into a paid subscriber based on their engagement and usage behavior.

The project demonstrates a complete supervised machine learning workflow, including data cleaning, exploratory data analysis, feature engineering, model comparison, cross-validation, hyperparameter tuning, and probability-based prediction.

> **Note:** This project uses a small synthetic dataset of 100 users and is intended for learning and portfolio demonstration rather than production deployment.

---

## 🎯 Problem Statement

### Business Problem

Subscription-based businesses have a large number of free users, but only a portion eventually convert into paid subscribers.

The objective of this project is to answer:

**Can we predict whether a free user will convert into a paid subscriber based on their engagement behavior?**

### Machine Learning Problem

This is a **supervised binary classification** problem.

### Target Variable

`Converted`

| Value | Meaning                       |
| ----- | ----------------------------- |
| `0`   | User did not convert          |
| `1`   | User became a paid subscriber |

---

## 💼 Business Use Cases

The model can help businesses:

* Identify high-potential free users
* Prioritize conversion campaigns
* Personalize offers and messaging
* Improve marketing efficiency
* Understand engagement patterns associated with conversion
* Segment users based on predicted conversion probability

---

## 📊 Dataset Features

The dataset contains demographic, engagement, trial, and support-related attributes.

| Feature                | Description                          |
| ---------------------- | ------------------------------------ |
| `Age`                  | User age                             |
| `Days_Since_Signup`    | Number of days since registration    |
| `Sessions`             | Number of sessions                   |
| `Visits`               | Number of visits                     |
| `Features_Used`        | Number of product features used      |
| `Avg_Session_Minutes`  | Average session duration             |
| `Trial_Days_Used`      | Number of trial days used            |
| `Support_Interactions` | Number of support interactions       |
| `Sessions_Per_Day`     | Sessions relative to signup duration |
| `Visits_Per_Session`   | Visits relative to sessions          |
| `Features_Per_Session` | Features used relative to sessions   |
| `Engagement_Score`     | Composite engagement metric          |
| `Converted`            | Target variable                      |

`User_ID` is excluded from modeling because it is an identifier rather than a predictive feature.

---

## 🔄 Machine Learning Workflow

```text
Raw User Data
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Train / Test Split
      ↓
┌──────────────────────────────┐
│ Logistic Regression          │
│ Decision Tree                │
│ Random Forest                │
└──────────────────────────────┘
      ↓
Model Comparison
      ↓
5-Fold Cross-Validation
      ↓
Hyperparameter Tuning
      ↓
Final Model
      ↓
Conversion Probability
```

---

## 🧹 Data Preprocessing

The preprocessing workflow includes:

* Removing duplicate records
* Detecting missing numerical values
* Median imputation for missing numerical values
* Stratified train/test splitting
* Feature scaling for Logistic Regression

The project uses an **80/20 train-test split** with `random_state=42`.

---

## 🔍 Exploratory Data Analysis

EDA is used to investigate:

* Conversion distribution
* Average engagement metrics by conversion status
* Feature distributions
* Relationships between engagement behavior and conversion

Visualizations include target-distribution plots and feature-level boxplots.

---

## 🛠️ Feature Engineering

Additional behavioral features are created to provide more meaningful signals to the models:

```text
Sessions_Per_Day
Visits_Per_Session
Features_Per_Session
Engagement_Score
```

The `Engagement_Score` combines multiple behavioral indicators, including sessions, visits, features used, and trial usage.

---

## 🤖 Machine Learning Models

Three classification algorithms are compared.

### 1. Logistic Regression

Used as an interpretable baseline model for binary classification.

A `StandardScaler` is included through a Scikit-learn pipeline because Logistic Regression benefits from comparable feature scales.

### 2. Decision Tree

Used to capture non-linear relationships and rule-based decision patterns within user behavior.

### 3. Random Forest

An ensemble model consisting of multiple decision trees.

The initial configuration includes:

```text
n_estimators = 300
max_depth = 8
min_samples_split = 5
class_weight = "balanced"
```

---

## 📏 Model Evaluation

The models are evaluated using multiple metrics:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Confusion Matrix
* Classification Report
* ROC Curve

### Cross-Validation

Because the dataset contains only 100 users, the project uses **5-fold Stratified Cross-Validation** with ROC-AUC as the scoring metric.

This provides a more robust evaluation than relying only on one train/test split.

---

## ⚙️ Hyperparameter Tuning

`GridSearchCV` is used to optimize the Random Forest model.

The following hyperparameters are explored:

```text
n_estimators
max_depth
min_samples_split
min_samples_leaf
```

The optimization objective is:

```text
ROC-AUC
```

using 5-fold stratified cross-validation.

---

## 🔎 Model Interpretability

Random Forest feature importance is calculated to understand which features contributed most to the model's predictions.

> Feature importance indicates association with model predictions; it does not establish that a feature causally drives subscription conversion.

---

## 🎯 Prediction Output

The final workflow generates a conversion probability for each user.

Example output:

| Column                   | Description                              |
| ------------------------ | ---------------------------------------- |
| `Actual_Converted`       | Actual conversion outcome                |
| `Conversion_Probability` | Estimated probability of conversion      |
| `Predicted_Converted`    | Binary prediction using a 0.50 threshold |

Users can then be sorted according to their predicted conversion probability.

---

## 💡 Business Interpretation

The predicted probabilities can support different customer strategies.

### High Predicted Probability

Potentially prioritize users for conversion-focused campaigns.

### Medium Predicted Probability

Experiment with:

* Personalized offers
* Better onboarding
* Engagement campaigns
* Product education

### Low Predicted Probability

Focus on improving engagement and onboarding before aggressively targeting conversion.

> These strategies are business experimentation hypotheses, not guarantees of user behavior.

---

## 📁 Project Structure

```text
subscription-conversion-prediction/
│
├── data/
│   └── subscription_conversion_100_users.csv
│
├── notebooks/
│   └── Subscription_Conversion_Prediction_ML_Project.ipynb
│
├── models/
│   └── README.md
│
├── src/
│   └── README.md
│
├── requirements.txt
├── README.md
└── .gitignore
```

The current implementation is primarily contained in a Jupyter/Google Colab notebook. The additional folders provide a structure that can later be expanded into a more production-oriented project.

---

## 🧰 Tech Stack

**Language**

* Python

**Data Analysis**

* Pandas
* NumPy

**Visualization**

* Matplotlib

**Machine Learning**

* Scikit-learn

**Environment**

* Jupyter Notebook
* Google Colab

---

## 🧠 Concepts Demonstrated

This project demonstrates practical understanding of:

* Binary Classification
* Data Preprocessing
* Exploratory Data Analysis
* Feature Engineering
* Stratified Train/Test Splitting
* Feature Scaling
* Logistic Regression
* Decision Trees
* Random Forest
* Model Comparison
* Cross-Validation
* Hyperparameter Optimization
* ROC-AUC
* Confusion Matrix
* Feature Importance
* Probability-Based Predictions
* Business Interpretation of ML Outputs

---

## ⚠️ Limitations

This project is designed as a **learning and portfolio implementation**, not a production-ready prediction system.

The dataset contains only 100 users, so model performance may vary substantially depending on the train/test split.

A production implementation would require:

* A significantly larger historical dataset
* Time-based validation where appropriate
* Data leakage checks
* Probability calibration
* Robust preprocessing pipelines
* Production monitoring
* Data drift detection
* Periodic model retraining
* Business-defined decision thresholds
* Evaluation using real-world outcomes

---

## 🚀 Future Improvements

Potential extensions include:

* Increase the training dataset
* Add real subscription and behavioral data
* Build automated preprocessing pipelines
* Test additional classification algorithms
* Perform feature selection
* Calibrate predicted probabilities
* Optimize classification thresholds based on business costs
* Add SHAP-based explainability
* Build a Streamlit prediction interface
* Save the trained model using `joblib`
* Create an inference API
* Add automated tests and CI/CD
* Monitor model performance after deployment

---

## 🔁 Reproducibility

The project uses fixed random seeds where applicable.

Train/test split:

```python
test_size = 0.20
random_state = 42
stratify = y
```

Cross-validation uses a 5-fold `StratifiedKFold` configuration with a fixed random state.

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/subscription-conversion-prediction.git

cd subscription-conversion-prediction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
notebooks/Subscription_Conversion_Prediction_ML_Project.ipynb
```

The notebook can also be executed using **Google Colab**.

---

## 📦 Requirements

```text
pandas
numpy
matplotlib
scikit-learn
jupyter
```

---

## 📈 Results

Model performance is calculated directly within the notebook using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Cross-validation ROC-AUC

Performance numbers are intentionally not hard-coded into this README so that the reported results remain tied to the actual notebook execution.

---

## 👨‍💻 Author

**Arsh**

Machine Learning | Data Analytics | Business Intelligence

---

## 📄 License

This project is intended for educational and portfolio purposes.

If you plan to distribute or adapt the project, consider adding an appropriate open-source license such as the MIT License.
