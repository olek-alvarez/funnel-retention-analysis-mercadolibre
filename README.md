# Funnel & Retention Analysis – MercadoLibre (SQL)

## Objective
Analyze the user conversion funnel and retention behavior to identify where users drop off and uncover opportunities to improve conversion rates and long-term engagement.

---

## Business Context
As a Product Analyst at MercadoLibre, the goal is to understand user behavior across the purchase journey and answer key business questions:

- Where do we lose the most users in the funnel?
- What are the conversion rates between each stage?
- How does retention evolve over time?
- How do these metrics vary by country and device?

---

## Dataset
The analysis is based on two main tables:

- **mercadolibre_funnel**: user events across the purchase journey  
- **mercadolibre_retention**: user activity for cohort-based retention analysis  

---

## Process

### Funnel Analysis
- Built a multi-step funnel using SQL (CTEs)
- Calculated conversion rates between stages:
  - first_visit → select_item
  - select_item → add_to_cart
  - add_to_cart → purchase
- Identified drop-off points across the funnel

### Retention Analysis
- Performed cohort analysis using signup date
- Calculated retention at:
  - D7, D14, D21, D28
- Segmented results by country and device

---

## Methodology (SQL Tasks)

### 1. Retention by Country
- Calculated cumulative active users at D7, D14, D21, and D28
- Used CASE statements and DISTINCT counts to avoid duplicates
- Filtered data between Jan–Aug 2025

### 2. Retention Rates (%)
- Converted user counts into retention percentages
- Applied ROUND and NULLIF to ensure accuracy and avoid division errors

### 3. Cohort Definition
- Created monthly cohorts using signup date
- Used DATE_TRUNC and aggregation to assign users to cohorts

### 4. Cohort Retention Analysis
- Built cohort-based retention using CTEs
- Calculated retention at D7, D14, D21, D28
- Analyzed trends across time, country, and device

---

## Tools
- SQL (CTEs, aggregations, cohort analysis)
- Data analysis techniques (funnel & retention analysis)

---

## Key Results

### Funnel Analysis
- 76.9% of users reach product selection, but only **1.25% complete a purchase**
- The largest drop-off occurs between **product selection and add-to-cart**

### Retention Analysis
- Retention is high at **D7 (~86%)** but drops sharply to **~2–3% by D28**
- Early cohorts show stronger retention than recent ones

---

## Key Insights

- Users show high initial interest but low purchase conversion
- The add-to-cart stage represents the main friction point
- Retention declines significantly after the first 2 weeks
- Countries like **Mexico and Peru** show better retention performance

---

## Business Recommendations

- Improve the **add-to-cart experience** to reduce drop-off
- Optimize checkout flow (costs, shipping, payment options)
- Implement early-stage retention strategies (onboarding, reminders)
- Analyze low-performing countries to identify localized issues
