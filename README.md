# Data-Mining-OnlineShope

# 🛒 Online Retail Customer Churn Prediction
### From Raw Transactions to Customer Retention Intelligence

<p align="center">
  <img src="https://img.shields.io/badge/PROJECT-Data%20Mining-306998?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/PYTHON-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/WORKFLOW-CRISP--DM-7C3AED?style=for-the-badge" />
  <img src="https://img.shields.io/badge/STATUS-In%20Progress-F59E0B?style=for-the-badge" />
</p>

<p align="center">
  <b>Turning customer transaction data into actionable insights for predicting churn and improving customer retention.</b>
</p>

---

## 📌 Project Overview

Customer churn is one of the most important challenges in e-commerce. Customers may gradually reduce their purchases, become less active, or stop buying altogether without providing any explicit warning.

For an online store, losing an existing customer can mean losing future revenue and wasting previous investments in customer acquisition.

The goal of this project is to develop a data-driven system that analyzes historical purchasing behavior, identifies early warning signs of customer churn, and predicts which customers are most likely to stop purchasing.

Instead of simply analyzing past sales, this project aims to transform raw transaction records into customer-level behavioral features, a classification model, and a risk-based customer prioritization system that can support retention decisions.

> **Core mission:** Identify customers who are approaching churn before their inactivity becomes a long-term business problem.

## 🎯 Business Problem

The business currently has access to historical transaction data, but it does not have a reliable, directly provided churn label for each customer.

This creates several challenges:

- Which customers are becoming less active?
- How can we distinguish normal purchasing gaps from potential churn?
- Which behavioral patterns indicate an increased risk of losing a customer?
- Can we predict churn before it happens?
- Which customers should the business prioritize for retention campaigns?
- How can transaction data be converted into practical business decisions?

The project addresses these questions through data exploration, data preparation, feature engineering, supervised machine learning, and model evaluation.

## 🎯 Project Objectives

| Objective | Business Value |
|---|---|
| Analyze customer purchasing behavior | Understand how customers interact with the store |
| Clean and validate transaction data | Improve the reliability of analytical results |
| Identify churn-related behavioral patterns | Discover early warning signals |
| Build a classification model | Estimate the probability of customer churn |
| Evaluate predictive performance | Measure how reliably the model identifies at-risk customers |
| Calculate customer risk scores | Compare customers by their estimated churn risk |
| Prioritize the 500 highest-risk customers | Create a practical starting point for retention campaigns |
| Translate predictions into business insights | Support data-driven customer retention decisions |

## 🗂️ Dataset

**Dataset:** [Online Retail — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail)

The project uses historical transactions from a UK-based online retail business. The dataset contains transaction-level information that can be transformed into customer-level behavioral features.

### Main attributes

| Attribute | Description |
|---|---|
| `InvoiceNo` | Invoice identifier; may also indicate a cancellation |
| `StockCode` | Product identifier |
| `Description` | Product description |
| `Quantity` | Number of units purchased; negative values may indicate returns |
| `InvoiceDate` | Date and time of the transaction |
| `UnitPrice` | Price per unit |
| `CustomerID` | Customer identifier; may be missing |
| `Country` | Customer's country |

The original dataset does not directly provide a customer churn label. Therefore, a major part of the project is defining a measurable churn target from historical purchasing activity.

*Note: The final usable columns, customer coverage, and record counts will be verified during data understanding and preparation.*

## 🧠 Churn Definition & Prediction Strategy

A machine learning model needs a clearly defined target. In this project, churn is operationally defined using a customer's purchasing activity after a reference date.

### Proposed labeling strategy

- **Observation window:** The 180 days preceding the reference date.
- **Prediction window:** The 90 days following the reference date.
- **Churned customer:** A customer who makes no new valid purchase during the 90-day prediction window.
- **Active customer:** A customer who makes at least one valid purchase during that window.

The reference date will be selected and validated based on the available transaction timeline.

### Example

Suppose the reference date is 1 January.

- Customer A makes valid purchases during the next 90 days → **Active**
- Customer B makes no valid purchases during the next 90 days → **Churned**

The model uses only information available before the reference date to predict the outcome of the following 90 days.

This separation is essential because using future purchasing information as an input feature would introduce **data leakage** and make the model's performance misleading.

**Important:** This definition is a practical modeling assumption, not proof that a customer has permanently abandoned the store.

## 🔬 Methodology — CRISP-DM

The project follows the six phases of the CRISP-DM methodology, a structured framework for data-mining projects.

### 1. Business Understanding

**Purpose:** Define the business problem and translate it into measurable analytical objectives.

Planned activities:

- Define customer churn and the prediction horizon.
- Identify business goals and project constraints.
- Determine which customers and decisions the model should support.
- Define success criteria for model evaluation.
- Establish the objective of prioritizing the 500 highest-risk customers.

**Deliverable:** A documented business problem, churn definition, and project success criteria.

### 2. Data Understanding

**Purpose:** Understand the structure, quality, and limitations of the transaction data.

Planned activities:

- Load the dataset and inspect its dimensions and columns.
- Review data types and statistical summaries.
- Measure missing values and duplicate records.
- Analyze canceled invoices and returned products.
- Investigate negative quantities and unusual prices.
- Examine the distribution of transactions across customers and time.
- Explore purchasing frequency, recency, monetary value, and customer activity.

**Deliverable:** A data-quality assessment and an initial understanding of customer purchasing behavior.

### 3. Data Preparation

**Purpose:** Convert raw transaction records into a reliable customer-level modeling dataset.

Planned activities:

- Handle missing customer identifiers according to the analytical task.
- Investigate duplicate records and inconsistent values.
- Separate or appropriately handle canceled transactions and returns.
- Validate quantities, prices, dates, and transaction identifiers.
- Calculate valid purchase amounts.
- Aggregate transaction-level records into customer-level features.
- Create the churn target using the defined future observation window.
- Check for data leakage and prepare the final modeling dataset.

#### Planned feature engineering

| Feature | Meaning |
|---|---|
| `Recency` | Days since the customer's most recent valid purchase before the reference date |
| `Frequency` | Number of valid purchases or distinct purchase invoices |
| `Monetary` | Total valid purchase value during the observation window |
| `AverageOrderValue` | Average value of a valid purchase invoice |
| `PurchaseInterval` | Typical time between purchases |
| `UniqueProducts` | Number of distinct products purchased |
| `ActiveDays` | Number of distinct days with valid purchases |
| `Churn` | Target label derived from purchasing activity after the reference date |

These are proposed features. Their final definitions and inclusion will depend on data validation and the modeling design.

**Deliverable:** A clean, customer-level dataset containing predictive features and a clearly defined target.

### 4. Modeling

**Purpose:** Train machine learning models to classify customers according to their future churn risk.

The main task is **supervised classification**, because the project constructs a target label from future purchasing behavior.

Planned activities:

- Separate predictive features from the target.
- Split the data into training and testing sets using a time-aware strategy where feasible.
- Establish a simple baseline.
- Train and compare suitable classification algorithms.
- Tune model parameters when justified.
- Address class imbalance if it affects model performance.
- Generate churn probabilities or risk scores for eligible customers.

Potential algorithms include:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

The final model will be selected based on evaluation results rather than assuming that one algorithm is always the best.

**Deliverable:** A trained classification model and customer-level churn risk scores.

### 5. Evaluation

**Purpose:** Determine whether the model is reliable and useful for the business objective.

Planned evaluation methods:

| Metric | Why it matters |
|---|---|
| Precision | How many customers flagged as high-risk actually churned? |
| Recall | How many churned customers did the model identify? |
| F1-score | How well does the model balance precision and recall? |
| ROC-AUC | How well does the model distinguish between the two classes across thresholds? |
| PR-AUC | How effectively does the model identify the positive class, particularly when classes are imbalanced? |
| Confusion Matrix | What types of classification errors does the model make? |

The evaluation will also consider the business cost of false positives and false negatives.

For example, failing to identify a customer who is about to churn may mean losing a retention opportunity, while incorrectly flagging an active customer may lead to unnecessary marketing expenditure.

**Deliverable:** A documented model comparison, evaluation results, and a justified model-selection decision.

### 6. Deployment

**Purpose:** Turn the analytical results into a practical customer-retention workflow.

Planned activities:

- Apply the selected model to eligible customer records.
- Calculate and rank customer churn risk scores.
- Identify the 500 highest-risk customers, subject to sufficient eligible customer coverage.
- Produce a structured output for business review.
- Suggest retention actions based on observed customer behavior.
- Document how the model could be integrated into a future business workflow.

Possible retention actions include personalized offers, targeted reminders, loyalty incentives, and follow-up campaigns.

**Deliverable:** A prioritized customer-risk list, actionable business recommendations, and a documented deployment approach.

*Deployment in a live production environment is a future extension unless implemented as part of the project.*

## 🛠️ Technology Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data cleaning, transformation, and aggregation |
| NumPy | Numerical operations and data manipulation |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Scikit-learn | Classification, preprocessing, model selection, and evaluation |
| Jupyter Notebook | Interactive analysis, experimentation, and documentation |
| Git & GitHub | Version control and project documentation |

## 📊 Expected Outputs

The project aims to produce the following analytical outputs:

1. A structured analysis of transaction data quality.
2. A cleaned and validated customer-level dataset.
3. A reproducible churn-labeling procedure.
4. An analysis of customer purchasing behavior and potential churn indicators.
5. A comparison of classification models.
6. An evaluation report with appropriate performance metrics.
7. A churn risk score for each eligible customer.
8. A ranked list of the 500 highest-risk customers, when sufficient eligible customers are available.
9. Business recommendations for prioritizing customer-retention efforts.

These are planned deliverables, not claims that all outputs have already been completed.

## ⚠️ Key Challenges & Considerations

### Data quality

Canceled orders, product returns, missing customer IDs, duplicates, and unusual values can distort customer behavior metrics if they are not handled carefully.

### No predefined churn label

The target must be constructed from future purchasing activity, with a clear and consistent definition of a valid purchase.

### Class imbalance

If churned customers are relatively uncommon, accuracy alone may give a misleading impression of model quality.

### Data leakage

Features must be calculated using information available before the reference date. Future purchasing behavior must only be used to construct the target.

### Temporal validation

Customer behavior can change over time. A time-aware evaluation strategy is preferable when the dataset supports it.

### Business usefulness

A model with strong statistical performance is not automatically useful. The final system should help the business identify actionable customers and allocate retention resources more effectively.

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

Replace the placeholders with your actual GitHub repository URL and folder name.

### 2. Create a virtual environment (recommended)

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

If a `requirements.txt` file is available:

```bash
pip install -r requirements.txt
```

The planned core dependencies include:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyterlab
```

### 4. Open JupyterLab

```bash
jupyter lab
```

### 5. Load the dataset

Update the file path to match the location of the CSV file in your local repository.

```python
import pandas as pd

df = pd.read_csv("../OnlineRetail.csv")

print(df.shape)
print(df.head())
print(df.info())
```

Continue with data understanding, preparation, feature engineering, modeling, and evaluation in the planned order.

## 🗺️ Project Roadmap

- [x] Define the business scenario and main objective.
- [x] Select the initial dataset.
- [x] Establish a preliminary churn definition.
- [ ] Complete data understanding and quality assessment.
- [ ] Clean and validate transaction records.
- [ ] Engineer customer-level features.
- [ ] Construct and validate the churn target.
- [ ] Establish a baseline classification model.
- [ ] Train and compare candidate algorithms.
- [ ] Evaluate and select the final model.
- [ ] Generate customer churn risk scores.
- [ ] Prioritize the 500 highest-risk customers.
- [ ] Document business recommendations.
- [ ] Prepare the final analytical report.

The checklist reflects the planned workflow and should be updated as each stage is completed and verified.

## 🔮 Future Improvements

Potential extensions after the core project include:

- Explainable predictions using feature importance or SHAP.
- More detailed customer segmentation.
- Personalized retention strategies for different customer groups.
- Cost-sensitive decision thresholds based on retention campaign budgets.
- Time-based monitoring for changes in churn behavior.
- A simple dashboard for exploring customer risk.
- An automated pipeline for scoring new transaction data.

These improvements are optional extensions and are not required for the initial classification objective.

## 📚 References

- **Dataset:** [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)
- **Methodology:** [CRISP-DM — Cross-Industry Standard Process for Data Mining](https://www.ibm.com/docs/en/spss-modeler)
- **Data Analysis:** [Pandas Documentation](https://pandas.pydata.org/docs/)
- **Machine Learning:** [Scikit-learn Documentation](https://scikit-learn.org/stable/)

---

<p align="center">
  <b>Built with Python, driven by data, focused on customer retention.</b>
  <br>
  <sub>A practical data-mining project connecting customer behavior analysis with predictive machine learning.</sub>
</p>
