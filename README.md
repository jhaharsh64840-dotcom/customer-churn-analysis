# Customer Churn Analysis and Customer Intelligence

## 📌 Project Overview

Customer churn is a major challenge for subscription-based businesses. Losing customers can reduce recurring revenue, increase customer acquisition costs, and negatively affect business growth.

This project analyzes customer subscription data to understand churn patterns, identify potential risk factors, evaluate customer retention, and generate actionable business insights.

Using Python, Pandas, SQL (SQLite), and data visualization libraries, this project explores customer demographics, subscription plans, support complaints, cancellation patterns, and revenue at risk.

The objective is to help businesses understand customer behavior and make data-driven decisions to improve retention.

## 🎯 Business Objectives

* Calculate customer churn and retention rates.
* Analyze churn across different subscription plans.
* Identify monthly customer cancellation trends.
* Calculate average revenue per user (ARPU).
* Estimate revenue associated with churned customers.
* Analyze customer tenure and support complaints.
* Investigate the relationship between support escalations and churn.
* Categorize customers into low, medium, and high churn-risk groups.
* Visualize customer behavior and identify potential areas for improvement.

## 🛠️ Tools and Technologies

| Tool             | Purpose                                               |
| ---------------- | ----------------------------------------------------- |
| Python           | Data analysis and feature engineering                 |
| Pandas           | Data cleaning, transformation, and aggregation        |
| NumPy            | Numerical operations and feature creation             |
| SQLite           | Database storage and SQL queries                      |
| SQL              | Data retrieval, aggregation, and database exploration |
| Matplotlib       | Data visualization                                    |
| Seaborn          | Statistical visualization                             |
| Jupyter Notebook | Interactive analysis and documentation                |

## 📂 Project Structure

```text
customer-churn-analysis/
│
├── churn_analysis.ipynb
├── customer_churn.db
├── customer_churn_data_raw.xlsx
├── exported_churn_data.csv
└── README.md
```

**Note:** The database and Excel file are source-data options used by the notebook. The exported CSV is generated during analysis. Include the relevant files in your repository only if you have permission to share them and they contain no sensitive customer information.

## 📊 Dataset Description

The notebook works with three main data tables.

### 1. Customer Data

Contains customer demographic and location information.

Example attributes include:

* Customer ID
* Customer name
* Date of birth
* Gender
* State
* Country

### 2. Subscription Data

Contains information about customer subscriptions and billing.

Example attributes include:

* Customer ID
* Subscription start date
* Renewal date
* Cancellation date
* Subscription plan
* Contract type
* Monthly charges
* Churn score

### 3. Customer Support Data

Contains information about customer support interactions.

Example attributes include:

* Customer ID
* Complaint date
* Complaint count
* Support escalations

*The exact available columns depend on the supplied source files.*

## 🔄 Project Workflow

### Step 1: Data Import and Database Exploration

* Connect to the SQLite database.
* Retrieve database table names.
* Inspect table structures and column names.
* Import database tables into Pandas DataFrames.
* Support creating a local SQLite database from an Excel workbook.

### Step 2: Data Cleaning and Preparation

The project performs several data preparation tasks:

* Renames columns for clarity.
* Removes unnecessary columns.
* Converts date columns into datetime format.
* Standardizes gender categories.
* Fills missing country values using state-to-country mappings.
* Examines customer support records and duplicate customer IDs.

### Step 3: Feature Engineering

New analytical features are created from existing data.

**Churn Flag**

Customers with a recorded cancellation date are classified as churned.

* `1` = Churned customer
* `0` = Customer without a recorded cancellation date

**Customer Tenure**

Calculates the number of days between subscription start and cancellation. For customers without a cancellation date, the current date is used.

**Churn Risk Category**

Customers are categorized according to their churn score:

* Low risk: Score below 50
* Medium risk: Score from 50 to below 70
* High risk: Score of 70 or above

### Step 4: Data Integration

Customer, subscription, and support datasets are combined using customer IDs.

The project uses Pandas merge operations to integrate the datasets and prepares a consolidated dataset for further analysis.

It also calculates complaint counts and examines duplicate support records before merging.

### Step 5: Exploratory Data Analysis

The project investigates several business metrics.

| Metric                       | Purpose                                                        |
| ---------------------------- | -------------------------------------------------------------- |
| Churn Rate                   | Measures the proportion of customers who have churned          |
| Retention Rate               | Measures the proportion of customers who have not churned      |
| Churn by Plan                | Compares churn rates across subscription plans                 |
| Average Revenue per User     | Calculates average monthly charges per customer record         |
| Average Customer Tenure      | Measures subscription duration in days                         |
| Revenue at Risk              | Estimates monthly charges associated with churned customers    |
| Escalation Rate              | Measures the proportion of records marked as escalated         |
| Average Complaints per User  | Examines customer support complaint frequency                  |
| Escalation–Churn Correlation | Evaluates the correlation between support escalation and churn |

### Step 6: Data Visualization

The project uses Matplotlib and Seaborn to explore customer behavior through visualizations, including:

* Monthly churn trends.
* Churn rates by subscription plan.
* Churn rates by state.
* Correlation heatmaps.
* Pair plots.
* Customer charge comparisons by plan, gender, and churn-risk category.

Pivot tables are also used to summarize churn and monthly charges across subscription plans.

### Step 7: Exporting Results

The consolidated dataset is exported to CSV format for further analysis, reporting, or use in visualization tools.

## 📈 Key Business Questions

This project is designed to answer the following questions:

1. What proportion of customers have churned?
2. Which subscription plans have higher churn rates?
3. How does customer churn change over time?
4. What is the average monthly charge per customer?
5. How much monthly charge value is associated with churned customers?
6. How long do customers typically remain subscribed?
7. How frequently do customers raise support complaints?
8. Is there a relationship between support escalations and customer churn?
9. Which customers fall into the high churn-risk category?
10. How does churn vary across different states?

## 💡 Business Applications

The analysis can help businesses:

* Identify subscription plans with comparatively high churn.
* Monitor customer cancellations over time.
* Investigate customer support issues.
* Identify customer segments that may need retention initiatives.
* Estimate recurring monthly charges associated with churned customers.
* Develop targeted customer engagement strategies.
* Improve subscription and customer experience decisions.

The results indicate where further investigation may be useful. Additional analysis is required before concluding that a particular factor causes churn.

## ⚙️ Installation and Setup

### Prerequisites

Install Python and Jupyter Notebook on your computer.

Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

SQLite support is available through Python's built-in `sqlite3` module, so a separate installation is not normally required.

### Run the Project

**1. Clone the repository**

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your actual GitHub repository URL.

**2. Open the project directory**

```bash
cd customer-churn-analysis
```

**3. Ensure the required source data is available**

Place the appropriate source file in the project directory:

* `customer_churn.db`, or
* `customer_churn_data_raw.xlsx` if you need to create the database.

The notebook expects these filenames unless you modify the relevant file paths.

**4. Launch Jupyter Notebook**

```bash
jupyter notebook
```

**5. Open and run the notebook**

Open `churn_analysis.ipynb` and execute the cells in order.

## ⚠️ Important Notes

* The notebook uses SQLite and Python for database access and analysis.
* Most data cleaning, merging, feature engineering, and analysis are performed using Pandas.
* The notebook also demonstrates SQL queries executed through SQLite.
* The revenue-at-risk calculation sums monthly charges for churned customers. It is an estimate of associated monthly charges, not a calculation of realized financial losses.
* The correlation between support escalations and churn does not establish causation.
* Customer records and support records should be checked carefully before aggregation to avoid double-counting.
* The notebook's source datasets are required to reproduce the complete analysis.

## 🚀 Future Improvements

Potential extensions include:

* Writing more analytical SQL queries using joins, CTEs, window functions, and aggregations.
* Building a Power BI dashboard for customer churn monitoring.
* Performing cohort-based retention analysis.
* Comparing churn across customer segments and contract types.
* Investigating the financial impact of customer churn.
* Developing a predictive churn model using machine learning.
* Adding automated data-quality checks and reproducible reporting.

## 👨‍💻 Author

**Harsh Jha**

Aspiring Business Analyst | Data Analytics | SQL | Python | Power BI

Interested in transforming raw data into meaningful business insights and supporting data-driven decision-making.

---

⭐ If you find this project useful, consider starring the repository.
