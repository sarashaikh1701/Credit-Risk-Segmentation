# Credit Risk Segmentation  
## Alteryx & Power BI


## Overview

This project demonstrates a rule-based credit risk segmentation workflow built in **Alteryx** and visualised in **Power BI**.

Using the German Credit dataset, I designed a transparent scoring framework to segment customers into **Low**, **Medium**, and **High** risk tiers based on financial stability, loan exposure, and repayment duration.

The goal was to simulate how a consulting team might structure credit data into decision-ready portfolio insights.


## Business Context

Given a retail credit portfolio, key questions include:

- How is risk distributed across customers?
- Where is capital exposure concentrated?
- Are higher-risk customers associated with larger or longer loans?

Instead of building a predictive model, this project focuses on **structured risk segmentation and portfolio analysis**, prioritising transparency and explainability.


## Tools Used

- **Alteryx Designer** – Data preparation and risk scoring
- **Power BI Desktop** – Portfolio visualisation
- **DAX** – Exposure concentration metric


## Alteryx Workflow

The workflow follows a structured pipeline:

**Input → Cleaning → Feature Engineering → Risk Scoring → Segmentation → Aggregation → Output**


### 1. Data Preparation

- Removed unnecessary fields
- Standardised data types
- Replaced missing values in *Saving accounts* and *Checking account* with a consistent category

This ensured downstream scoring logic remained stable and reproducible.


### 2. Risk Feature Engineering

Each qualitative indicator was converted into a numeric risk contribution.

#### Liquidity Indicators

- Lower savings → higher risk weight
- Lower checking balance → higher risk weight
- Unknown values assigned moderate risk

**Purpose:** Simulate short-term financial buffer strength.


#### Housing Stability

- Own → lowest risk
- Free → moderate risk
- Rent → higher financial burden

**Purpose:** Reflect structural financial stability.


#### Employment Level

Job category (0–3) was mapped to a stability gradient:

- Lower skill levels → higher risk weight
- Higher skill levels → lower risk weight

**Purpose:** Capture employment-driven income stability.


#### Exposure & Duration

Loan size and repayment duration were segmented into increasing risk brackets.

- Larger loan → higher capital exposure
- Longer duration → greater repayment uncertainty


### 3. Composite Risk Score

All engineered components were aggregated into a total risk score.

The total score was then mapped into:

- **Low Risk**
- **Medium Risk**
- **High Risk**

This produces a simplified, explainable scorecard model.


### 4. Portfolio Aggregation

Using the **Summarize tool** in Alteryx, the portfolio was grouped by Risk Tier to calculate:

- Number of customers
- Total exposure
- Average loan size
- Average duration

The final dataset was exported for visualisation in Power BI.


## Power BI Dashboard

The dashboard presents a portfolio-level risk overview.

### Key Metrics

- Total Portfolio Exposure: ~3M
- Total Customers: 1000
- High Risk Exposure: 20%


### Key Observations

- Medium-risk customers represent the largest share of exposure.
- High-risk customers are a small segment by count.
- However, they account for approximately 20% of total capital.
- High-risk customers also have significantly larger average loan sizes and longer repayment durations.

This indicates capital concentration within the high-risk segment.
