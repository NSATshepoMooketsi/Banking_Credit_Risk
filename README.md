# Banking_Credit_Risk
Developed an interactive Power BI Credit Risk Dashboard using a star schema, Power Query, and DAX to analyze loan performance, customer demographics, default and delinquency trends, income segments, and lending risk. Demonstrates data modelling, KPI development, and business intelligence reporting for data-driven decision-making.
# Data Modelling

The original dataset consisted of a single flat file containing **29 attributes**, where loan, borrower and location information were stored in a single table. To improve scalability, reduce data redundancy and follow dimensional modelling best practices, the data was transformed into a **star schema model**.

## Star Schema Design

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

## Example: Loan Dimension

The original dataset contained over **1,000 loan records**, many of which repeated the same loan attributes.

After selecting the loan-related fields:

- Loan Intent
- Loan Grade
- Loan Term (Months)

duplicate combinations were removed, reducing the dimension to **166 unique loan profiles**.

A surrogate **Loan_ID** was then generated to uniquely identify each loan attribute combination.

This allows the fact table to store only the surrogate key rather than repeatedly storing descriptive loan information for every transaction.

---

## Why a Star Schema?

Although the Power BI model size increased slightly after introducing additional dimensions, relationships and measures, this is expected. Power BI stores report metadata, visuals, relationships and DAX calculations in addition to the compressed data model.

The purpose of the star schema is **not simply to reduce file size**, but to create a model that is easier to maintain, faster to query and more scalable.

### Benefits

✔ Reduced repeated attribute values across the model

✔ Improved model organisation through logical business entities

✔ Simplified DAX calculations by separating facts from descriptive dimensions

✔ Improved filter propagation through one-to-many relationships

✔ Created a scalable data model that can easily accommodate additional attributes

✔ Followed dimensional modelling best practices commonly used in enterprise data warehouses

---

## Data Model

The final solution follows a traditional star schema consisting of:

```
                 Dim Person
                      │
                      │
Dim Loan ─────── Fact Credit Risk ─────── Dim Location
```

This modelling approach provides a clean separation between descriptive dimensions and measurable business facts, resulting in a model that is easier to understand, extend and analyse.
