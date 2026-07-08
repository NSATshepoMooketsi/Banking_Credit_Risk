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
## 2. Key Insights 📈
###  2.1 Performing Loans and Borrower demographics
- Customer base is dominated by Mid-Career to Pre-Retirement customers, 23% of which have dependents.
- Customer distribution by gender is balanced.
- Seniors have the highest churn rate due to competition, the general trend applies for all customer groups.
###  2.1.2 Dashboard Preview 📊
![Dashboard](Images/Customer_Demographics_Loyalty.png)
