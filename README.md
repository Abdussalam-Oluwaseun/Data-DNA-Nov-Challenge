# E-commerce Customer Loyalty Analysis
## Complete Documentation

---

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Data Dictionary](#data-dictionary)
3. [Methodology](#methodology)
4. [Key Metrics & Definitions](#key-metrics-definitions)
5. [RFM Analysis Framework](#rfm-analysis-framework)
6. [DAX Measures Reference](#dax-measures-reference)
7. [Customer Segmentation Logic](#customer-segmentation-logic)
8. [Dashboard Guide](#dashboard-guide)
9. [Appendix](#appendix)

---

## Executive Summary

### Project Overview
This analysis examines customer loyalty patterns for a global software retailer that sells subscriptions and add-ons across analytics, design, collaboration, and AI products. The primary objective is to identify loyal customers (repeat buyers) and determine which channels and promotional campaigns drive their repeat purchases.

### Dataset Overview
- **Time Period**: 2024 - 2025
- **Total Customers**: 4,000 loyal customers (all with 2+ purchases)
- **Total Transactions**: 48,000 events
- **Products**: Subscription-based software (Monthly, Annual, One-time)
- **Geographic Scope**: Global (multiple countries and currencies)

### Key Characteristics
- **Customer Purchase Frequency**: 2-27 purchases per customer (Mean: 12, Median: 12)
- **Customer Lifetime Value**: $106 - $37,830 (Mean: $7,958, Median: $7,159)
- **All customers in analysis are loyal** (minimum 2 purchases)
- **Refunded transactions**: Included in calculations with negative revenue impact

### Business Goals
1. Track sales and loyal-customer volumes over time
2. Highlight revenue drivers and repeat-purchase patterns
3. Show how discounts and pricing influence sales performance
4. Deliver clear insights that guide business strategy and stakeholder decisions

### Target Audience
- Business stakeholders
- Marketing teams
- Sales leadership
- Executive decision-makers

---

## Data Dictionary

### Original Data Sources

#### Customer Table (`df_customer`)
| Column | Description | Data Type |
|--------|-------------|-----------|
| `customer_id` | Unique ID for each customer | Text |
| `signup_date` | When the customer signed up | Date |
| `region` | State/province/region | Text |
| `currency_preference` | Preferred currency if the customer chose one | Text |
| `segment` | Customer segment (e.g., Student, SMB, Enterprise) | Text |
| `acquisition_channel` | How the customer first found or was acquired by the business | Text |
| `age_band` | Age group (e.g., 18–24) | Text |
| `currency` | Currency used for pricing on events | Text |
| `country` | Customer's country | Text |
| `country_latitude` | Customer's country centroid latitude coordinates | Decimal |
| `country_longitude` | Customer's country centroid longitude coordinates | Decimal |

#### Product Table
| Column | Description | Data Type |
|--------|-------------|-----------|
| `product_id` | Unique ID for each product/plan | Text |
| `product_name` | Product/plan name | Text |
| `category` | Product category (e.g., Analytics, Collaboration) | Text |
| `is_subscription` | Subscription vs one-time item | Boolean |
| `billing_cycle` | Monthly, Annual, or One-time | Text |
| `base_price_usd` | List price in USD before discounts/taxes | Decimal |
| `first_release_date` | Approximate "first availability" of the product family/plan | Date |

#### Events/Sales Table (`df_events`)
| Column | Description | Data Type |
|--------|-------------|-----------|
| `event_id` | Unique ID for each transaction-like record | Text |
| `event_type` | order (new sale) or invoice (renewal/billing) | Text |
| `event_date` | Timestamp when the event occurred | DateTime |
| `customer_id` | Customer on the event | Text |
| `product_id` | Product/plan on the event | Text |
| `country` | Customer location on the event | Text |
| `region` | Customer region on the event | Text |
| `channel` | Sales channel (Website, Direct Sales, etc.) | Text |
| `payment_method` | Payment type (Credit Card, Invoice, etc.) | Text |
| `currency` | Currency used for this event | Text |
| `fx_rate_to_usd` | Conversion rate used for USD amounts | Decimal |
| `quantity` | Number of seats/units | Integer |
| `unit_price_local` | Unit list price in local currency | Decimal |
| `discount_code` | Code applied to the event | Text |
| `discount_local` | Discount amount in local currency | Decimal |
| `tax_local` | Tax/VAT in local currency | Decimal |
| `net_revenue_local` | Net amount in local currency | Decimal |
| `net_revenue_usd` | Net amount converted to USD | Decimal |
| `is_refunded` | True/False if refunded | Boolean |
| `refund_datetime` | When refund happened | DateTime |
| `refund_reason` | Reason for refund | Text |

### Engineered Features

#### RFM Scores (Created in Python)
| Column | Description | Calculation Method | Values |
|--------|-------------|-------------------|---------|
| `recency_days` | Days since last purchase | `reference_date - last_purchase_date` | 0 - 730+ days |
| `recency_score` | Recency scoring (1-5) | Based on fixed day ranges | 1-5 |
| `purchase_count` | Total number of purchases per customer | Count of events per customer | 2-27 |
| `frequency_score` | Frequency scoring (1-5) | Based on purchase count ranges | 1-5 |
| `total_revenue` | Total revenue generated by customer | Sum of `net_revenue_usd` | $106 - $37,830 |
| `monetary_score` | Monetary value scoring (1-5) | Based on revenue ranges | 1-5 |
| `rfm_total_score` | Combined RFM score | `recency_score + frequency_score + monetary_score` | 3-15 |
| `customer_segment` | RFM-based segment classification | Logic-based segmentation | See segmentation logic |

#### Time-Based Features (Created in Power BI)
| Column | Description | Formula |
|--------|-------------|---------|
| `Year` | Year extracted from event_date | `YEAR(Events[event_date])` |
| `Month` | Month extracted from event_date | `MONTH(Events[event_date])` |
| `MonthYear` | Month-Year for time series | `FORMAT(Events[event_date], "MMM YYYY")` |

#### Customer Lifecycle Features (Created in Power BI)
| Column | Description | Logic |
|--------|-------------|-------|
| `Customer_Age_Days` | Days since customer signup | `DATEDIFF(signup_date, reference_date, DAY)` |
| `Lifecycle_Segment` | Customer maturity stage | 0-90 days: "Very New"<br>91-180 days: "New"<br>181-365 days: "Established"<br>365+ days: "Mature" |
| `Churn_Status` | Customer activity status | Based on recency_score:<br>Score 5-4: "Active"<br>Score 3: "Moderate"<br>Score 2: "Lapsing"<br>Score 1: "Churned" |

#### Revenue Features (Created in Power BI)
| Column | Description | Formula |
|--------|-------------|---------|
| `discount_usd` | Discount amount in USD | `Events[discount_local] * Events[fx_rate_to_usd]` |

#### Loyalty Classification
| Column | Description | Logic |
|--------|-------------|-------|
| `is_loyal` | Whether customer is loyal | `IF(purchase_count >= 2, TRUE, FALSE)` |
| `is_high_value` | Whether customer is high-value | `IF(monetary_score >= 4, TRUE, FALSE)` |
| `is_at_risk` | Whether customer is at risk | `IF(recency_score <= 2, TRUE, FALSE)` |

---

## Methodology

### 1. Data Cleaning & Preparation

#### Excel Power Query
- Loaded raw CSV files
- Checked for duplicates
- Validated data types
- Handled missing values
- Standardized text fields (e.g., channel names, country codes)

#### Python Processing
```python
# Reference date for recency calculations
reference_date = df_events['event_date'].max()

# RFM calculations performed on non-refunded, valid transactions
# Refunds kept in data with their negative revenue impact
```

### 2. RFM Analysis Framework

#### Recency Calculation
```python
# Step 1: Get last purchase date per customer
customer_recency = df_events.groupby('customer_id')['event_date'].max()

# Step 2: Calculate days since last purchase
recency_days = (reference_date - last_purchase_date).days

# Step 3: Assign score based on fixed ranges
# See scoring logic below
```

#### Frequency Calculation
```python
# Step 1: Count purchases per customer
customer_frequency = df_events.groupby('customer_id').size()

# Step 2: Assign score based on purchase count
# See scoring logic below
```

#### Monetary Calculation
```python
# Step 1: Sum total revenue per customer (including refunds)
customer_monetary = df_events.groupby('customer_id')['net_revenue_usd'].sum()

# Step 2: Assign score based on revenue ranges
# See scoring logic below
```

### 3. Scoring Logic

#### Recency Score (R)
| Score | Days Since Last Purchase | Description |
|-------|-------------------------|-------------|
| 5 | 0-30 days | Highly Active |
| 4 | 31-90 days | Active |
| 3 | 91-180 days | Moderate |
| 2 | 181-365 days | Lapsing |
| 1 | 365+ days | Churned |

```python
def assign_recency_score(days):
    if days <= 30: return 5
    elif days <= 90: return 4
    elif days <= 180: return 3
    elif days <= 365: return 2
    else: return 1
```

#### Frequency Score (F)
| Score | Purchase Count | Description |
|-------|----------------|-------------|
| 5 | 18+ purchases | Exceptional loyalty |
| 4 | 14-17 purchases | High frequency |
| 3 | 10-13 purchases | Good frequency |
| 2 | 2-9 purchases | Loyal/Repeat customer |
| 1 | 1 purchase | One-time buyer (excluded from this analysis) |

```python
def assign_frequency_score(count):
    if count >= 18: return 5
    elif count >= 14: return 4
    elif count >= 10: return 3
    elif count >= 2: return 2
    else: return 1
```

#### Monetary Score (M)
| Score | Total Revenue (USD) | Description |
|-------|-------------------|-------------|
| 5 | $15,000+ | VIP |
| 4 | $10,584 - $14,999 | High value |
| 3 | $7,159 - $10,583 | Medium-high value |
| 2 | $4,393 - $7,158 | Medium value |
| 1 | < $4,393 | Standard value |

```python
def assign_monetary_score(revenue):
    if revenue >= 15000: return 5
    elif revenue >= 10584: return 4
    elif revenue >= 7159: return 3
    elif revenue >= 4393: return 2
    else: return 1
```

### 4. Customer Segmentation Logic

**All customers in this analysis are loyal (purchase_count >= 2)**

Segments are assigned based on RFM scores:

```python
def assign_segment(row):
    rfm_score = row['rfm_total_score']
    recency = row['recency_score']
    frequency = row['frequency_score']
    monetary = row['monetary_score']
    
    # Champions: Best on all metrics
    if rfm_score >= 13 and recency >= 4 and frequency >= 4:
        return "Champions"
    
    # High-Value Loyal: High spending + decent activity
    elif monetary >= 4 and recency >= 3:
        return "High-Value Loyal"
    
    # Loyal Frequent: High frequency + decent recency
    elif frequency >= 4 and recency >= 3:
        return "Loyal Frequent"
    
    # At-Risk Loyal: Haven't purchased recently
    elif recency <= 2:
        if monetary >= 4:
            return "At-Risk High-Value"
        else:
            return "At-Risk Standard"
    
    # Standard Loyal: Everything else
    else:
        return "Standard Loyal"
```

#### Segment Definitions

| Segment | Criteria | Description | Strategic Priority |
|---------|----------|-------------|-------------------|
| **Champions** | RFM >= 13, R >= 4, F >= 4 | Best customers: Recent, frequent, high-value | Reward, retain, request referrals |
| **High-Value Loyal** | M >= 4, R >= 3 | High spenders who are reasonably active | Upsell premium features, VIP treatment |
| **Loyal Frequent** | F >= 4, R >= 3 | Frequent buyers, decent recency | Increase spend per transaction |
| **At-Risk High-Value** | R <= 2, M >= 4 | Valuable customers who haven't purchased recently | Win-back campaigns, special offers |
| **At-Risk Standard** | R <= 2, M < 4 | Lower-value customers at risk of churning | Low-cost retention efforts |
| **Standard Loyal** | All other loyal customers | Regular repeat customers | Standard marketing, engagement |

### 5. Data Export & Visualization

```python
# Export RFM results to CSV
rfm.to_csv('rfm_customer_segments.csv', index=False)

# Import into Power BI
# Create relationships: Customers[customer_id] → Events[customer_id]
# Build measures and visualizations
```

---

## Key Metrics & Definitions

### Customer Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **Total Customers** | Count of unique customers | `DISTINCTCOUNT(Customers[customer_id])` |
| **Loyal Customers** | Customers with 2+ purchases | `CALCULATE([Total Customers], Customers[purchase_count] >= 2)` |
| **New Customers per Month** | Customers acquired in the month | Count of customers where `MONTH(signup_date) = Selected Month` |
| **At-Risk Loyal Customers** | Loyal customers with R score <= 2 | `CALCULATE([Loyal Customers], Customers[recency_score] <= 2)` |
| **High-Value Loyal Customers** | Loyal customers with M score >= 4 | `CALCULATE([Loyal Customers], Customers[monetary_score] >= 4)` |
| **% Customers At Risk** | Percentage of customers at risk | `DIVIDE([At-Risk Loyal Customers], [Total Customers])` |
| **% High Value Customers** | Percentage of high-value customers | `DIVIDE([High-Value Loyal], [Total Customers])` |

### Revenue Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **Total Revenue** | Sum of all net revenue (excluding refunds) | `SUM(Events[net_revenue_usd])` filtered by `is_refunded = FALSE` |
| **Total Revenue by Loyal Customers** | Revenue from customers with 2+ purchases | Revenue filtered by loyal customers |
| **Revenue At Risk** | Revenue from at-risk customers | Revenue from customers with R score <= 2 |
| **Revenue High Value Customers** | Revenue from high-value customers | Revenue from customers with M score >= 4 |
| **Revenue Refunded** | Total refunded amount | `SUM(Events[net_revenue_usd])` where `is_refunded = TRUE` |
| **Refund Rate** | Percentage of revenue refunded | `DIVIDE([Revenue Refunded], [Total Revenue] + [Revenue Refunded])` |

### Order Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **Total Orders** | Count of non-refunded events | `COUNTROWS(Events)` filtered by `is_refunded = FALSE` |
| **Total Orders by Loyal Customers** | Orders from loyal customers | Orders filtered by loyal customers |
| **Total Unit Sold** | Sum of quantity sold | `SUM(Events[quantity])` |
| **Increase in Order per Month** | Month-over-month order growth | `[Total Orders] - [Previous Month Orders]` |
| **Count of Refunds** | Number of refunded transactions | `COUNTROWS(Events)` where `is_refunded = TRUE` |

### Engagement Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **Avg Days Since Last Purchase** | Average recency across all customers | `AVERAGE(Customers[recency_days])` |
| **Avg Days Since Last Purchase (At-Risk)** | Average recency for at-risk customers | Average recency_days where R <= 2 |
| **Average RFM Score** | Mean RFM total score | `AVERAGE(Customers[rfm_total_score])` |

### Discount Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **Most Used Discount Code** | Discount code used most frequently | `MODE(Events[discount_code])` or TOPN calculation |
| **Most Used Discount Avg Price** | Average discount amount for most used code | Average of discount amounts for top code |
| **Count of Customers Use Code** | Number of customers who used discounts | `DISTINCTCOUNT` of customer_id where discount_code exists |

### Comparison Metrics

| Metric | Definition | Formula/Logic |
|--------|------------|---------------|
| **vs Last Month** | Comparison to previous month | Current month value - previous month value |
| **vs Last Year** | Year-over-year comparison | Current value - same period last year |

---

## RFM Analysis Framework

### Understanding RFM

**RFM** is a customer segmentation technique that uses three dimensions:

- **Recency (R)**: How recently did the customer purchase?
- **Frequency (F)**: How often does the customer purchase?
- **Monetary (M)**: How much does the customer spend?

### Why RFM for Subscription Business?

1. **Recency predicts churn**: Customers who haven't renewed recently are at risk
2. **Frequency shows loyalty**: Multiple renewals indicate strong product-market fit
3. **Monetary identifies value**: High spenders deserve special attention and retention efforts

### RFM Score Interpretation

#### Total RFM Score Ranges
- **13-15**: Champions - Your best customers
- **10-12**: High-performing - Strong loyal base
- **7-9**: Average - Standard loyal customers
- **4-6**: At-risk - Need attention
- **3**: Lowest - Critical intervention needed

#### Individual Score Interpretation

**High Recency (R = 4-5)**
- Recently active
- Currently engaged
- Low churn risk

**Low Recency (R = 1-2)**
- Haven't purchased recently
- Churn risk
- Win-back needed

**High Frequency (F = 4-5)**
- Frequent renewals
- Strong product adoption
- Low churn likelihood

**Low Frequency (F = 1-2)**
- Few purchases
- Testing or uncertain
- Conversion opportunity

**High Monetary (M = 4-5)**
- High revenue contribution
- Premium customer
- High retention priority

**Low Monetary (M = 1-2)**
- Lower spending
- Upsell opportunity
- Cost-effective retention

### Segmentation Strategy

| Segment | R | F | M | Action Strategy |
|---------|---|---|---|-----------------|
| Champions | High | High | High | Reward loyalty, request referrals, beta test new features |
| High-Value Loyal | High | Med+ | High | VIP treatment, exclusive offers, account management |
| Loyal Frequent | High | High | Med | Increase transaction value, premium upsells |
| Standard Loyal | Med | Med | Med | Standard marketing, engagement campaigns |
| At-Risk High-Value | Low | Any | High | Priority win-back, personalized outreach, special discounts |
| At-Risk Standard | Low | Any | Low | Low-cost automated campaigns, survey for feedback |

---

## DAX Measures Reference

### Customer Measures

```dax
// Total Customers
Total Customers = DISTINCTCOUNT(Customers[customer_id])

// Loyal Customers (2+ purchases)
Loyal Customers = 
CALCULATE(
    [Total Customers],
    Customers[purchase_count] >= 2
)

// At-Risk Loyal Customers
At-Risk Loyal Customers = 
CALCULATE(
    [Total Customers],
    Customers[recency_score] <= 2
)

// High-Value Loyal Customers
High-Value Loyal Customers = 
CALCULATE(
    [Total Customers],
    Customers[purchase_count] >= 2,
    Customers[monetary_score] IN {4, 5}
)

// New Customers per Month
New Customer per Month = 
CALCULATE(
    [Total Customers],
    DATESMTD(Customers[signup_date])
)

// % Customers At Risk
% Customers At Risk = 
DIVIDE(
    [At-Risk Loyal Customers],
    [Total Customers],
    0
)

// % High Value Customers
% High Value Customers = 
DIVIDE(
    [High-Value Loyal Customers],
    [Total Customers],
    0
)
```

### Revenue Measures

```dax
// Total Revenue (excluding refunds)
Total Revenue = 
CALCULATE(
    SUM(Events[net_revenue_usd]),
    Events[is_refunded] = FALSE
)

// Total Revenue by Loyal Customers
Total Revenue by Loyal Customers = 
CALCULATE(
    [Total Revenue],
    Customers[purchase_count] >= 2
)

// Revenue At Risk
Revenue At Risk Customers = 
CALCULATE(
    SUM(Customers[total_revenue]),
    Customers[recency_score] <= 2
)

// Revenue High Value Customers
Revenue High Value Customers = 
CALCULATE(
    SUM(Customers[total_revenue]),
    Customers[monetary_score] IN {4, 5}
)

// Revenue Refunded
Revenue Refunded = 
CALCULATE(
    SUM(Events[net_revenue_usd]),
    Events[is_refunded] = TRUE
)

// Refund Rate
Refund Rate = 
VAR TotalWithRefunds = [Total Revenue] + ABS([Revenue Refunded])
RETURN
    DIVIDE(ABS([Revenue Refunded]), TotalWithRefunds, 0)
```

### Order Measures

```dax
// Total Orders (non-refunded)
Total Orders = 
CALCULATE(
    COUNTROWS(Events),
    Events[is_refunded] = FALSE
)

// Total Orders by Loyal Customers
Total Orders by Loyal Customers = 
CALCULATE(
    [Total Orders],
    Customers[purchase_count] >= 2
)

// Total Unit Sold
Total Unit Sold = 
CALCULATE(
    SUM(Events[quantity]),
    Events[is_refunded] = FALSE
)

// Increase in Order per Month
Increase in Order per Month = 
VAR CurrentMonth = [Total Orders]
VAR PreviousMonth = 
    CALCULATE(
        [Total Orders],
        DATEADD(Events[event_date], -1, MONTH)
    )
RETURN
    CurrentMonth - PreviousMonth

// Count of Refunds
Count of Refunds = 
COUNTROWS(
    FILTER(Events, Events[is_refunded] = TRUE)
)
```

### Engagement Metrics

```dax
// Avg Days Since Last Purchase
Avg Days Since Last Purchase = 
AVERAGE(Customers[recency_days])

// Avg Days Since Last Purchase (At-Risk)
Avg Days Since Last Purchase (At-Risk) = 
CALCULATE(
    AVERAGE(Customers[recency_days]),
    Customers[recency_score] <= 2
)
```

### Discount Metrics

```dax
// Most Used Discount Code
Most Used Discount Code = 
CALCULATE(
    FIRSTNONBLANK(Events[discount_code], 1),
    TOPN(
        1,
        VALUES(Events[discount_code]),
        CALCULATE(COUNTROWS(Events)),
        DESC
    )
)

// Most Used Discount Avg Price
Most Used Discount Avg Price = 
VAR TopCode = [Most Used Discount Code]
RETURN
    CALCULATE(
        AVERAGE(Events[discount_usd]),
        Events[discount_code] = TopCode
    )

// Count of Customers Use Code
Count of Customers Use Code = 
CALCULATE(
    DISTINCTCOUNT(Events[customer_id]),
    NOT(ISBLANK(Events[discount_code]))
)
```

### Time Comparison Measures

```dax
// vs Last Month
vs Last Month = 
VAR CurrentValue = [Total Revenue]  // or any other measure
VAR PreviousMonth = 
    CALCULATE(
        [Total Revenue],
        DATEADD(Events[event_date], -1, MONTH)
    )
RETURN
    CurrentValue - PreviousMonth

// vs Last Year
vs Last Year = 
VAR CurrentValue = [Total Revenue]
VAR LastYear = 
    CALCULATE(
        [Total Revenue],
        SAMEPERIODLASTYEAR(Events[event_date])
    )
RETURN
    CurrentValue - LastYear
```

### Insight Card Measures

```dax
// Dynamic Insight Card
Dynamic Insight Card = 
VAR AtRiskPct = [% Customers At Risk]
VAR HighValuePct = [% High Value Customers]
VAR ChampPct = 
    DIVIDE(
        CALCULATE([Total Customers], Customers[customer_segment] = "Champions"),
        [Total Customers],
        0
    )
VAR Insight = 
    SWITCH(
        TRUE(),
        AtRiskPct > 0.40,
            "🚨 HIGH CHURN RISK" & UNICHAR(10) & UNICHAR(10) &
            FORMAT(AtRiskPct, "0%") & " of customers at risk" & UNICHAR(10) &
            "Immediate retention action needed",
        
        HighValuePct < 0.20,
            "💰 UPSELL OPPORTUNITY" & UNICHAR(10) & UNICHAR(10) &
            "Only " & FORMAT(HighValuePct, "0%") & " are high-value" & UNICHAR(10) &
            "Focus on customer value growth",
        
        ChampPct > 0.15,
            "🏆 STRONG PERFORMANCE" & UNICHAR(10) & UNICHAR(10) &
            FORMAT(ChampPct, "0%") & " are Champions" & UNICHAR(10) &
            "Maintain engagement strategies",
        
        "📊 BALANCED PORTFOLIO" & UNICHAR(10) & UNICHAR(10) &
        "Continue current strategies" & UNICHAR(10) &
        "Monitor segment shifts"
    )
RETURN Insight
```

---

## Customer Segmentation Logic

### Segment Distribution (Expected)

Based on RFM scoring methodology:

| Segment | RFM Criteria | Expected % | Description |
|---------|-------------|-----------|-------------|
| Champions | Score >= 13, R >= 4, F >= 4 | ~10-15% | Top-tier customers |
| High-Value Loyal | M >= 4, R >= 3 | ~15-20% | High spenders |
| Loyal Frequent | F >= 4, R >= 3 | ~15-20% | Frequent buyers |
| Standard Loyal | Mid-range scores | ~30-40% | Regular customers |
| At-Risk High-Value | R <= 2, M >= 4 | ~5-10% | Valuable at-risk |
| At-Risk Standard | R <= 2, M < 4 | ~10-15% | Standard at-risk |

### Segment Actions & KPIs

#### Champions
**Characteristics**: RFM >= 13, Recent, Frequent, High-value
**Action**:
- Reward programs and VIP benefits
- Request referrals and testimonials
- Beta testing opportunities
- Exclusive early access

**KPIs to Track**:
- Retention rate (should be 95%+)
- Referral conversion rate
- Lifetime value growth
- Net Promoter Score (NPS)

#### High-Value Loyal
**Characteristics**: High spending, reasonable activity
**Action**:
- Dedicated account management
- Premium support
- Exclusive webinars/events
- Custom enterprise solutions

**KPIs to Track**:
- Revenue per customer
- Contract renewal rate
- Upsell success rate
- Engagement frequency

#### Loyal Frequent
**Characteristics**: High frequency, moderate spending
**Action**:
- Increase average transaction value
- Bundle offers and upsells
- Premium tier promotions
- Feature adoption campaigns

**KPIs to Track**:
- Average order value trend
- Product adoption rate
- Upgrade conversion rate
- Purchase frequency stability

#### Standard Loyal
**Characteristics**: Regular repeat customers
**Action**:
- Standard marketing campaigns
- Educational content
- Community engagement
- Loyalty rewards

**KPIs to Track**:
- Churn rate
- Engagement metrics
- Product usage patterns
- Support ticket frequency

#### At-Risk High-Value
**Characteristics**: Valuable but inactive
**Action**:
- Priority win-back campaigns
- Personalized outreach from CSM
- Special "We miss you" offers (10-20% discount)
- Phone calls or personal emails
- Customer satisfaction surveys

**KPIs to Track**:
- Win-back success rate
- Time to re-engagement
- Revenue recovered
- Churn prevention rate

#### At-Risk Standard
**Characteristics**: Lower value, inactive
**Action**:
- Automated email campaigns
- Discount incentives (5-10%)
- Re-engagement surveys
- Product education content

**KPIs to Track**:
- Campaign response rate
- Cost per re-activation
- ROI of win-back efforts
- Final churn rate

---

## Dashboard Guide

### Dashboard Structure

The analysis is presented across 4 main pages:

1. **Overview** - Executive summary and key metrics
2. **Segment Analysis** - Deep dive into customer segments
3. **Customer Detail** - Granular customer-level insights
4. **Product Analysis** - Product and channel performance

### Page 1: Overview

**Purpose**: High-level business health snapshot

**Key Visuals**:
- Total Customers (Card)
- Total Revenue (Card)
- At-Risk Loyal Customers count and percentage (Cards)
- High-Value Loyal Customers count and percentage (Cards)
- Customer Segment distribution (Table)
- Distribution of Billing Cycle by Orders/Revenue (Donut chart)
- Acquisition Channel by RFM Segment (Stacked bar chart)
- Revenue and customer trends over time (Line charts)

**Key Questions Answered**:
- What is our overall customer base size?
- What percentage of customers are at risk?
- How much revenue is at risk?
- Which segments drive the most value?
- How are customers distributed across billing cycles?

### Page 2: Segment Analysis

**Purpose**: Understand segment performance and characteristics

**Key Visuals**:
- Segment performance matrix (Table with counts, revenue, avg metrics)
- RFM score distribution (Histogram)
- Channel performance by segment (Clustered column)
- At-risk customer breakdown by segment (Funnel)
- Product preferences by segment (Matrix)

**Key Questions Answered**:
- Which segments are growing/declining?
- What channels bring high-value segments?
- Which products are popular with Champions?

---

## Appendix

### File Structure
```
/Test/
├── README.md (this file)
├── rfm_customer_segments.csv (exported RFM results)
├── rfm.csv (intermediate RFM data)
├── Manufacturing_Line_Productivity.xlsx
├── data_dictionary.csv
├── RFM Analysis.ipynb (Jupyter notebook with analysis)
└── output/ (directory for analysis outputs)
```

### Key Files Description

- **README.md**: Complete documentation of the analysis
- **rfm_customer_segments.csv**: Final RFM customer segments with all scores and classifications
- **RFM Analysis.ipynb**: Python notebook containing all RFM calculations and data processing
- **data_dictionary.csv**: Data dictionary for reference tables

### Contact & Support

For questions or clarifications about this analysis, please reach out to the Data Analytics team.

### Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-11-20 | Initial release with complete RFM analysis framework |

---

**Last Updated**: November 20, 2025
