# Banking_Credit_Risk 📊
*About Project*
Developed an interactive Power BI Credit Risk Dashboard using a star schema, Power Query, and DAX to analyze loan performance, customer demographics, default and delinquency trends, income segments, and lending risk. Demonstrates data modelling, KPI development, and business intelligence reporting for data-driven decision-making.


# 1. Data Modelling & Dataset

The original dataset consisted of a single flat file containing **29 attributes**, where loan, borrower and location information were stored in a single table. To improve scalability, reduce data redundancy the data was transformed into a **star schema model**.

## 1.1 Star Schema Design

The source data was separated into logical business entities:

- **Fact Credit Risk** – Stores loan transactions and measurable business metrics.
- **Dim Person** – Contains borrower demographics and financial attributes.
- **Dim Loan** – Contains descriptive loan information such as purpose, grade and loan term.
- **Dim Location** – Contains geographic information including city, state and country.

Each dimension was created by:

1. Selecting the relevant attributes from the source dataset.
2. Removing duplicate attribute combinations.
3. Creating a surrogate key using an index.
4. Renaming the index to the entity identifier (e.g. `Person_ID`, `Loan_ID`, `Location_ID`).
5. Linking each dimension back to the fact table using one-to-many relationships.

---

## 1.2 Example: Loan Dimension

The original dataset contained over **1,000 loan records**, many of which repeated the same loan attributes.

After selecting the loan-related fields:

- Loan Intent
- Loan Grade
- Loan Term (Months)

Duplicate combinations were removed, reducing the dimension to **166 unique loan profiles**.

A surrogate **Loan_ID** was then generated to uniquely identify each loan attribute combination.

This allows the fact table to store only the surrogate key rather than repeatedly storing descriptive loan information for every transaction.

---

## 1.3 Data Model

The final solution follows a traditional star schema consisting of:

```
                 Dim Person
                      │
                      │
Dim Loan ─────── Fact Credit Risk ─────── Dim Location
```
This modelling approach provides a clean separation between descriptive dimensions and measurable business facts, resulting in a model that is easier to understand, extend and analyse.

---
# 2. Key Insights 📈
##  2.1 Customer Insights: Performing Loans
- Middle Class, Upper Middle Class and Affluent borrowers account for the largest share of the performing loan portfolio.
- Lower Middle Class borrowers exhibit the highest average Debt-to-Income (DTI) and Loan-to-Income (LTI) ratios among the major income segments.
- Borrower default rates decline as income class increases which indicates lower credit risk among higher-income segments.
- Prior delinquency rates are highest among the Working Class and Lower Working Class segments.
- Higher default rates are generally associated with higher Debt-to-Income (DTI) and Loan-to-Income (LTI) ratios across income classes.
- Average credit utilization remains relatively consistent across income classes and DTI/LTI segments, suggesting limited differentiation between customer groups.
- Borrowers with a previous default history exhibit substantially higher current default rates than borrowers with no previous defaults.
###  2.1.2 Dashboard Preview 📊
![Dashboard](Images/Customer_Demographics_Loyalty.png)
