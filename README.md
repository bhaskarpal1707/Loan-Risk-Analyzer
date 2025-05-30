# Loan Risk Analyzer: A Deep Dive into Financial Risk, Fraud Detection, and Customer Behavior

---

## 🔍 Project Overview

This project leverages **Exploratory Data Analysis (EDA)** to derive actionable business insights from a comprehensive loan dataset. The analysis aims to improve loan approval processes by reducing default risk, detecting fraudulent applications, and understanding borrower behavior.

---

## 🎯 Objectives

1. **Assess Financial Risk**  
   Evaluate borrower creditworthiness to reduce loan default risk.

2. **Detect Fraud**  
   Spot anomalies or red flags indicative of potential fraudulent applications.

3. **Understand Customer Behavior**  
   Segment customers based on financial traits and behavior patterns to inform policy design.

---

## 🧩 Business Domain

The project operates in the **financial services domain**, particularly within the **retail lending** and **loan underwriting** function of banks and financial institutions.

---

## 💡 Business Problems Solved

| Problem | EDA Contribution |
|--------|------------------|
| **Reduce Loan Default Risk** | Identified key risk drivers like `CreditScore`, `RiskScore`, `DebtToIncomeRatio`. |
| **Fraud Detection** | Flagged suspicious patterns (e.g., high income + multiple defaults). |
| **Understand Customer Behavior** | Clustered users based on employment, income, loan habits. |
| **Improve Loan Approval Accuracy** | Found strongest predictors for `LoanApproved`. |
| **Optimize Interest Rate Strategy** | Linked interest rate variance to customer risk profiles. |

---

## 🧪 Tools & Technologies Used

- **Excel**: Initial data cleanup and structure checks  
- **Jupyter Notebook**: Interactive EDA  
- **Python Libraries**:
  - `pandas`, `numpy` for data wrangling
  - `matplotlib`, `seaborn` for visualization

---

## 📁 Dataset

**Source**: [Kaggle: Financial Risk for Loan Approval](https://www.kaggle.com/datasets/lorenzozoppelletto/financial-risk-for-loan-approval/data)  
**Rows**: 20,000  
**Columns**: 36  

Key Features:
- `CreditScore`, `RiskScore`, `LoanAmount`, `Income`, `NetWorth`
- Behavioral indicators: `PaymentHistory`, `CreditInquiries`, `LoanPurpose`
- Flags: `LoanApproved`, `BankruptcyHistory`, `PreviousLoanDefaults`

---

## 🔄 Workflow & Methodology

### 1. Define the Domain  
Retail loan underwriting and credit risk analysis.

### 2. Select the Business Problems  
Focused on minimizing default, identifying fraud, and boosting approval efficiency.

### 3. Source the Dataset  
Curated dataset from Kaggle, mimicking real-world loan applications.

### 4. Clean the Dataset  
Performed missing value checks, type corrections, and formatted dates using:
- **Excel** for initial scan
- **Python** (`pandas`) for data integrity and transformations

### 5. EDA Breakdown

#### 🟢 Univariate Analysis
- **Age**: Peak in mid-30s; younger applicants less frequent.
- **RiskScore**: Most users fall between 45–60.
- **LoanPurpose**: 'Home' and 'Education' dominate applications.
- **LoanApproved**: ~24% approval rate — indicates stringent filtering.

#### 🟡 Bivariate Analysis
- **CreditScore vs LoanApproval**: Higher credit scores are directly tied to approval.
- **RiskScore vs InterestRate**: Riskier applicants are charged higher interest.
- **EmploymentStatus vs Income**: 'Employed' shows significantly higher income than 'Unemployed' or 'Retired'.

#### 🔵 Multivariate Analysis
- Applicants with:
  - High `DebtToIncomeRatio` + Low `CreditScore` + Short `JobTenure` → High default probability
  - High `Assets`, `NetWorth`, and `PaymentHistory` → Likely to be approved

---

## 🔍 Specialized Analyses

### 🛡️ Risk Assessment Analysis

**Insights:**

- 🔸 Applicants with **RiskScore below 45** are **twice as likely** to be denied loans. This metric is a reliable early indicator of risk.
- 🔸 A **DebtToIncomeRatio > 0.4** consistently correlates with a higher risk of default. This group should face stricter scrutiny or higher interest rates.
- 🔸 **CreditScore and PaymentHistory** are strong predictors of approval. Borrowers with a **CreditScore above 600 and PaymentHistory > 25 months** had a loan approval rate above 70%.
- 🔸 Customers with **short Credit History (<5 years)** and **low Job Tenure (<2 years)** form a high-risk group, even if their income is moderate to high.

**Business Takeaway:**  
Use a multi-factor approval model combining `RiskScore`, `DebtToIncomeRatio`, `CreditScore`, and `PaymentHistory` to reduce defaults and segment applicants more precisely.

**Visual Tools Used:**  
- Risk Tier Histograms  
- Risk vs LoanAmount/InterestRate Scatterplots  
- Correlation Heatmaps  

---

### 🚨 Fraud Detection Analysis

**Insights:**

- ⚠️ Applicants reporting **AnnualIncome > $100,000** but with **CreditScore < 500** and prior defaults are strong fraud candidates.
- ⚠️ Suspicious spikes in `NetWorth` without corresponding growth in `TotalAssets` or `SavingsAccountBalance` hint at fabricated declarations.
- ⚠️ A cluster of users had **0 Credit Inquiries**, **0 Open Credit Lines**, and **high loan requests** — potentially synthetic identities or staged profiles.
- ⚠️ **High PaymentHistory but low MonthlyDebtPayments** in some rejected applications may indicate underreported liabilities or front-loaded payments to appear creditworthy.

**Business Takeaway:**  
Flag applicants with data inconsistencies for manual review. A simple fraud scoring engine could cross-validate income, asset, and credit data points.

**Visual Tools Used:**  
- Boxplots for Income vs CreditScore  
- Anomaly scatterplots  
- Outlier detection using z-score & IQR  

---

### 👥 Customer Behavior Analysis

**Insights:**

- 👤 **Employed professionals aged 30–45** with a bachelor’s or master’s degree make up the **most reliable borrower segment**. They show high PaymentHistory and consistent income.
- 🧓 **Retired or unemployed applicants** with low liabilities often have high `TotalAssets`, indicating asset-rich but income-poor profiles. Good for secured loans, not personal loans.
- 💳 High **CreditCardUtilizationRate (>0.5)** is a sign of financial stress — applicants in this group are 60% more likely to be rejected.
- 🏠 Customers with **‘Home’ loan purposes** and `Mortgage` status show better long-term behavior, possibly due to collateral.
- 🔄 Applicants with **JobTenure > 7 years** and a stable credit line history are the **least risky group** overall.

**Segment Profiles Identified:**

| Segment | Key Traits | Strategy |
|--------|------------|----------|
| Young Earners | Age < 30, High Utilization, Low Credit History | Offer low-limit starter loans with education |
| Risk Managers | High JobTenure, High NetWorth, Good PaymentHistory | Fast-track approval with premium services |
| Credit Builders | Medium Income, 0–1 Credit Lines, No Defaults | Encourage secured credit cards or small loans |
| Asset-Rich Retirees | Low Income, High Assets, Low Liabilities | Target reverse mortgage or investment loans |

**Business Takeaway:**  
Use behavioral segmentation to design tailored financial products — from risk-based pricing to targeted loan types and educational outreach.

**Visual Tools Used:**  
- Violin plots for Utilization Rate  
- KDE plots for NetWorth by EmploymentStatus  
- Bar charts and pie charts for loan purposes and demographics  

---

## 📌 Key Insights & Recommendations

1. **Default Risk Reduction**  
   Screen out low `CreditScore` & high `DebtToIncomeRatio` applicants early.

2. **Fraud Pattern Detection**  
   Combine behavioral (e.g., `PaymentHistory`) with financial features for anomaly detection.

3. **Approval Optimization**  
   Leverage `RiskScore`, `PaymentHistory`, and `NetWorth` to improve prediction accuracy.

4. **Customer Segmentation**  
   Tailor loan products to well-defined segments based on education, job, and spending patterns.

5. **Interest Rate Strategy**  
   Offer **risk-adjusted rates** — rewarding low-risk customers and offsetting risk with premium rates.

---

## 📈 Project Outcome

✔ Improved risk profiling for loan decisions  
✔ Early fraud flagging system  
✔ Customer behavior insights for targeted offerings  
✔ Recommendation engine potential for personalized rates  

---

## 📂 Folder Structure
loan-risk-fraud-insights/
├── EDA.ipynb                # Jupyter notebook with full analysis
├── Loan.csv                 # Dataset used for EDA
├── README.md                # Project documentation
├── visuals/                 # Saved graphs and plots
└── requirements.txt         # Required Python libraries



