# E-commerce Customer Loyalty Analysis
## Complete Documentation

---

## Table of Contents
1. [Data Story & Key Insights](#data-story--key-insights)
2. [Executive Summary](#executive-summary)
3. [Data Dictionary](#data-dictionary)
4. [Methodology](#methodology)
5. [Key Metrics & Definitions](#key-metrics-definitions)
6. [RFM Analysis Framework](#rfm-analysis-framework)
7. [DAX Measures Reference](#dax-measures-reference)
8. [Customer Segmentation Logic](#customer-segmentation-logic)
9. [Dashboard Guide](#dashboard-guide)
10. [Appendix](#appendix)

---

## Data Story & Key Insights

### 📊 The Challenge

A global software retailer selling subscriptions and add-ons across analytics, design, collaboration, and AI products needed to understand their customer loyalty landscape. The key questions: **Who are their loyal customers? What drives them to keep coming back? And where should they focus their retention efforts?**

### 🔍 What I Discovered

#### The Good News: A Loyal Customer Base Driving Strong Revenue

My analysis of **4,000 customers** and **48,000 transactions** over 2024-2025 revealed a robust business with **$31.20 million in total revenue**. The standout finding? **100% of their customer base are repeat buyers** (2+ purchases), demonstrating strong product-market fit in the subscription software space.

**Revenue is growing year-over-year by 18.48%**, indicating healthy business expansion. However, the month-over-month decline of 14.25% signals potential seasonality that warrants monitoring.

#### Customer Segmentation: Where the Value Lives

Using RFM (Recency, Frequency, Monetary) analysis, we uncovered distinct customer segments with dramatically different value profiles:

| Segment | Customers | Revenue | Avg Days Since Purchase |
|---------|-----------|---------|-------------------------|
| **Champions** | 476 (12%) | $7.19M (23%) | 21 days |
| **High-Value Loyal** | 551 (14%) | $7.23M (23%) | 50 days |
| **Loyal Frequent** | 681 (17%) | $4.68M (15%) | 33 days |
| **Standard Loyal** | 2,227 (56%) | $11.80M (38%) | 47 days |
| **At-Risk Standard** | 61 (1.5%) | $244K (0.8%) | 234 days |
| **At-Risk High-Value** | 4 (0.1%) | $49K (0.2%) | 200 days |

**Key Insight**: Their **Champions and High-Value Loyal segments (26% of customers) generate 46% of total revenue**. These 1,027 customers are the backbone of the business.

#### The Warning Signs: At-Risk Customers

While the numbers are small, **65 loyal customers (1.63%) are at risk of churning**, representing **$293,260 in revenue at risk**. Most critically, **4 high-value customers** haven't purchased in over 200 days, with **$49,000 in potential revenue loss**.

**Action Required**: I recommend immediate personalized win-back campaigns for these 4 high-value at-risk customers could recover significant revenue with minimal effort.

#### Channel Performance: Organic is the Champion-Maker

My analysis of acquisition channels revealed a clear winner:

| Channel | Loyal Customers | Champions | Champion Rate |
|---------|----------------|-----------|---------------|
| **Organic** | 1,121 | Highest | Best ROI |
| Paid Search | 869 | Medium | Good volume |
| Social | 708 | Medium | Broad reach |
| Email | 664 | Medium | Engaged users |
| Affiliate | 447 | Lower | Niche audience |
| Retail Media | 191 | Lowest | Limited scale |

**Critical Finding**: I found that **Organic brings 639% more Champions than Retail Media**. This suggests significant ROI opportunity in SEO and content marketing investments over paid retail placements.

#### Product Insights: AI and Productivity Tools Lead

The most purchased products by loyal customers reveal clear preferences:

1. **Adobe Firefly Creative AI** - 3,810 purchases
2. **Power BI Pro** - 3,807 purchases
3. **Microsoft Copilot for Office** - 3,801 purchases
4. **ChatGPT Team** - 3,217 purchases
5. **Azure AI Studio** - 2,876 purchases

**Vendor Performance**: Microsoft dominates with **$9.82M revenue** (31.5% of total), followed by AI Tools ($5.33M) and Adobe ($4.08M).

**Insight**: I found that AI-powered tools are driving the majority of repeat purchases. I recommend they consider expanding AI product offerings and bundling strategies.

#### Billing Cycle Analysis: Annual Plans Win

The distribution of billing cycles shows a near-even split:
- **Annual Plans**: 24K orders (49.57%)
- **Monthly Plans**: 23K orders (48.46%)
- **One-time**: 1K orders (1.96%)

**However**, I found that annual subscribers demonstrate higher average revenue per customer and lower churn risk, making them more valuable despite similar order volumes.

#### The Refund Problem: Billing Errors Need Attention

**1,005 refunds** resulted in **$635,720 in revenue loss** (2.09% refund rate). Breaking down the reasons:

| Reason | Count | % of Refunds |
|--------|-------|--------------|
| **Billing Error** | 105 | 29% |
| Accidental Purchase | 94 | 26% |
| Duplicate Order | 87 | 24% |
| Service Dissatisfaction | 80 | 22% |

**Critical Issue**: I identified that **billing errors are the #1 refund reason**, representing a preventable revenue leak.

**Recommended Solutions**:
1. **Audit billing system** for recurring technical issues
2. **Implement pre-charge notifications** to customers
3. **Add confirmation steps** before processing payments
4. **Review payment gateway integration** for error patterns
5. **Create automated alerts** for unusual billing patterns

#### Geographic Distribution: US and UK Lead

Customer concentration by country:
1. **United States**: 1,202 customers, $2.67M revenue
2. **United Kingdom**: 585 customers, $1.69M revenue
3. **Canada**: 407 customers, $915K revenue
4. **Australia**: 401 customers, $1.06M revenue
5. **Germany**: 296 customers, $929K revenue

**Opportunity**: I found strong presence in English-speaking markets, with potential for expansion in European and APAC regions.

#### Discount Code Effectiveness

**WELCOME10** is the most used discount code with **2,730 uses** and an average discount of **$62.73**. Other popular codes include:
- LOYALTY15 (1,318 uses)
- SAVE5 (1,932 uses)
- BFCM10 (1,940 uses)
- NEWCUST... (1,947 uses)

**Insight**: I found that welcome and loyalty codes are driving repeat purchases, validating the promotional strategy.

---

### 🎯 Strategic Recommendations

Based on my analysis, I recommend the following actions:

#### 1. **Immediate: Win-Back Campaign for At-Risk High-Value Customers**
- **Target**: 4 At-Risk High-Value customers
- **Revenue at Risk**: $49,000
- **Action**: Personalized outreach with exclusive offer (15-20% discount)
- **Timeline**: Within 7 days
- **Expected Recovery**: 50-75% ($24K-$37K)

#### 2. **Short-term: Fix Billing Error Issues**
- **Problem**: 105 refunds due to billing errors ($63K+ estimated loss)
- **Action**: 
  - Audit payment processing system
  - Implement pre-charge email confirmations
  - Add double-confirmation for high-value transactions
- **Timeline**: 30 days
- **Expected Impact**: Reduce refunds by 25-30%

#### 3. **Medium-term: Double Down on Organic Acquisition**
- **Finding**: Organic channel produces 639% more Champions than Retail Media
- **Action**: 
  - Increase SEO/content marketing budget by 20-30%
  - Reduce Retail Media spend
  - Focus content on AI tools and productivity software
- **Timeline**: Next quarter
- **Expected Impact**: Higher quality customer acquisition at lower CAC

#### 4. **Medium-term: Promote Annual Billing**
- **Finding**: Annual subscribers show higher value and retention
- **Action**:
  - Offer incentives for monthly-to-annual conversion (2 months free)
  - Highlight annual savings prominently
  - Create annual-only exclusive features or support tiers
- **Timeline**: Next quarter
- **Expected Impact**: Improved customer lifetime value and reduced churn

#### 5. **Long-term: Expand AI Product Portfolio**
- **Finding**: AI tools (Adobe Firefly, Microsoft Copilot, ChatGPT, Azure AI) dominate top purchases
- **Action**:
  - Partner with emerging AI vendors
  - Create AI tool bundles
  - Develop AI-focused loyalty rewards
- **Timeline**: 6-12 months
- **Expected Impact**: Capture growing AI software market share

---

### 📈 Key Performance Indicators to Monitor

| KPI | Current Value | Target | Frequency |
|-----|---------------|--------|-----------|
| At-Risk Customer % | 1.63% | < 1.0% | Weekly |
| Revenue at Risk | $293K | < $200K | Weekly |
| High-Value Customer % | 25% | > 30% | Monthly |
| Refund Rate | 2.09% | < 1.5% | Monthly |
| Champion Segment % | 12% | > 15% | Quarterly |
| YoY Revenue Growth | 18.48% | > 20% | Quarterly |
| Organic Channel Share | 28% | > 35% | Quarterly |

---

### 💡 Summary: The Story in Numbers

| Metric | Value | Insight |
|--------|-------|---------|
| **$31.20M** | Total Revenue | Strong base, growing YoY |
| **4,000** | Loyal Customers | 100% repeat buyers |
| **476** | Champions | 12% drive 23% of revenue |
| **65** | At-Risk Customers | $293K revenue to protect |
| **1,121** | Organic Customers | Best channel for quality |
| **639%** | Organic vs Retail Media | Clear channel winner |
| **105** | Billing Error Refunds | #1 preventable issue |
| **$7,958** | Avg Customer Value | Healthy LTV foundation |

**The Bottom Line**: This is a healthy subscription business with strong customer loyalty. I've identified opportunities in protecting at-risk high-value customers, fixing billing errors, optimizing channel mix toward organic, and capitalizing on the AI tools trend. Executing on these four priorities can unlock the next phase of growth.

---

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
- How do segment characteristics differ?
- Where should we focus retention efforts?

### Page 3: Customer Detail

**Purpose**: Granular customer-level analysis

**Key Visuals**:
- Customer lifecycle distribution (Stacked area)
- Churn status breakdown (Donut)
- Geographic distribution by segment (Map or bar chart)
- Average days since last purchase by segment (Bar)
- Customer acquisition trends (Line chart)
- Top customers by revenue (Table with drill-through)

**Key Questions Answered**:
- How is our customer base aging?
- Where are our best customers located?
- What's the typical customer journey timeline?
- Which specific customers need immediate attention?
- How long do customers typically wait between purchases?

### Page 4: Product Analysis

**Purpose**: Product and channel performance insights

**Key Visuals**:
- Revenue by product category (Bar chart)
- Most popular products by segment (Matrix)
- Billing cycle performance (Clustered column)
- Discount code effectiveness (Table)
- Channel performance metrics (Matrix)
- Product mix by customer segment (Stacked bar)
- Refund analysis by product/channel (Table)

**Key Questions Answered**:
- Which products generate most revenue?
- Do annual plans bring higher customer value?
- Which discount codes drive repeat purchases?
- What's the refund rate by product?
- Which channels are most cost-effective?
- What products do loyal customers prefer?

### Dashboard Filters (Available on All Pages)

**Global Filters**:
- Date range (Year, Quarter, Month)
- Customer Segment
- Acquisition Channel
- Country/Region
- Product Category
- Billing Cycle

**Interactivity**:
- Click any visual to cross-filter others
- Drill-through from summary to detail
- Hover for detailed tooltips
- Export data to Excel for further analysis

### Dashboard Best Practices

**For Stakeholders**:
1. Start with Overview page for executive summary
2. Use filters to focus on specific time periods or segments
3. Click on segments in visuals to filter the entire page
4. Look for red indicators (at-risk metrics) requiring action

**For Analysis**:
1. Compare segments using the Segment Analysis page
2. Drill into specific customers on Customer Detail page
3. Analyze product performance on Product Analysis page
4. Use date filters to identify trends over time

**For Action Items**:
1. Identify at-risk high-value customers
2. Determine which channels to invest in
3. Find products with high attach rates for bundling
4. Spot discount codes that drive repeat purchases
5. Locate geographic opportunities for expansion

---

## Appendix

### A. Technical Specifications

**Tools Used**:
- **Data Cleaning**: Excel Power Query
- **RFM Calculations**: Python 3.x with pandas
- **Visualization**: Microsoft Power BI Desktop
- **Data Storage**: CSV files

**Data Volume**:
- Customer records: 4,000
- Transaction records: 48,000
- Product records: 101
- Time period: 2024-2025
- File size: ~8.1 MB (events table)

**Relationships**:
```
Customers (1) ─────────────── (*) Events
  customer_id                      customer_id

Products (1) ──────────────── (*) Events
  product_id                       product_id

Date Table (1) ────────────── (*) Events
  Date                             event_date
```

### B. Python Code for RFM Calculation

```python

# Load data
df_events = pd.read_csv('events.csv')
df_customer = pd.read_csv('customers.csv')

# Convert date columns
df_events['event_date'] = pd.to_datetime(df_events['event_date'])
df_customer['signup_date'] = pd.to_datetime(df_customer['signup_date'])

# Set reference date
reference_date = df_events['event_date'].max()

# ===== RECENCY CALCULATION =====
customer_recency = df_events.groupby('customer_id')['event_date'].max().reset_index()
customer_recency.columns = ['customer_id', 'last_purchase_date']
customer_recency['recency_days'] = (reference_date - customer_recency['last_purchase_date']).dt.days

def assign_recency_score(days):
    if days <= 30: return 5
    elif days <= 90: return 4
    elif days <= 180: return 3
    elif days <= 365: return 2
    else: return 1

customer_recency['recency_score'] = customer_recency['recency_days'].apply(assign_recency_score)

# ===== FREQUENCY CALCULATION =====
customer_frequency = df_events.groupby('customer_id').size().reset_index()
customer_frequency.columns = ['customer_id', 'purchase_count']

def assign_frequency_score(count):
    if count >= 18: return 5
    elif count >= 14: return 4
    elif count >= 10: return 3
    elif count >= 2: return 2
    else: return 1

customer_frequency['frequency_score'] = customer_frequency['purchase_count'].apply(assign_frequency_score)

# ===== MONETARY CALCULATION =====
customer_monetary = df_events.groupby('customer_id')['net_revenue_usd'].sum().reset_index()
customer_monetary.columns = ['customer_id', 'total_revenue']

def assign_monetary_score(revenue):
    if revenue >= 15000: return 5
    elif revenue >= 10584: return 4
    elif revenue >= 7159: return 3
    elif revenue >= 4393: return 2
    else: return 1

customer_monetary['monetary_score'] = customer_monetary['total_revenue'].apply(assign_monetary_score)

# ===== COMBINE RFM =====
rfm = customer_recency[['customer_id', 'recency_days', 'recency_score']]
rfm = rfm.merge(customer_frequency[['customer_id', 'purchase_count', 'frequency_score']], on='customer_id')
rfm = rfm.merge(customer_monetary[['customer_id', 'total_revenue', 'monetary_score']], on='customer_id')

# Calculate total RFM score
rfm['rfm_total_score'] = rfm['recency_score'] + rfm['frequency_score'] + rfm['monetary_score']

# ===== SEGMENTATION =====
def assign_segment(row):
    # All customers are loyal (purchase_count >= 2)
    if row['purchase_count'] < 2:
        return "Not Loyal"
    
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

rfm['customer_segment'] = rfm.apply(assign_segment, axis=1)

# ===== EXPORT =====
rfm.to_csv('rfm_customer_segments.csv', index=False)

# ===== VALIDATION =====
print("\n=== RFM SUMMARY ===")
print(rfm.head(10))
print("\n=== SEGMENT DISTRIBUTION ===")
print(rfm['customer_segment'].value_counts())
print("\n=== SEGMENT PERFORMANCE ===")
print(rfm.groupby('customer_segment').agg({
    'customer_id': 'count',
    'total_revenue': ['sum', 'mean'],
    'purchase_count': 'mean',
    'recency_days': 'mean',
    'rfm_total_score': 'mean'
}).round(2))

print("\n✅ RFM analysis complete!")
```

### C. Data Quality Checks

**Pre-Analysis Validation**:
- ✅ No duplicate customer_id in customer table
- ✅ No duplicate event_id in events table
- ✅ All event customer_ids exist in customer table
- ✅ All event product_ids exist in product table
- ✅ Date ranges are valid (no future dates)
- ✅ Revenue values are numeric
- ✅ Refund flags are boolean

**Post-Analysis Validation**:
- ✅ All customers have RFM scores
- ✅ RFM scores range from 1-5 as expected
- ✅ Total RFM scores range from 3-15
- ✅ All loyal customers have purchase_count >= 2
- ✅ Segment distribution is reasonable
- ✅ Revenue totals match between Python and Power BI

### D. Known Limitations

1. **Data Timeframe**: Analysis covers only 2024-2025, limiting long-term trend analysis
2. **Currency Conversion**: FX rates are point-in-time; actual rates may have fluctuated
3. **Geographic Precision**: Country centroids used instead of exact customer locations
4. **Seasonality**: Limited data may not capture full seasonal patterns
5. **Product Lifecycle**: New products may not have enough history for reliable patterns

### E. Future Enhancements

**Potential Additions**:
1. **Predictive Churn Model**: Machine learning to predict which customers will churn
2. **Customer Lifetime Value (CLV)**: Predict future customer value
3. **Cohort Analysis**: Analyze customer behavior by signup cohorts
4. **Product Affinity Analysis**: Identify products frequently bought together
5. **Channel Attribution**: Multi-touch attribution for customer journeys
6. **Sentiment Analysis**: Integrate support ticket or review data
7. **Real-time Alerts**: Automated notifications for at-risk high-value customers
8. **A/B Testing Framework**: Test retention strategies scientifically

**Technical Improvements**:
1. **Automated Data Pipeline**: Schedule daily/weekly refreshes
2. **Data Warehouse**: Migrate from CSV to proper database
3. **Version Control**: Track changes to RFM logic and segments
4. **API Integration**: Connect directly to operational systems
5. **Mobile Dashboard**: Power BI mobile optimization

### F. Glossary

| Term | Definition |
|------|------------|
| **Acquisition Channel** | The method by which a customer first discovered or was acquired (e.g., Organic, Paid Search, Email, Social, Direct, Referral, Affiliate, Retail Media) |
| **At-Risk Customer** | A loyal customer who hasn't purchased in 180+ days (recency score <= 2) |
| **Billing Cycle** | The frequency of subscription billing: Monthly, Annual, or One-time |
| **Champions** | Highest-value customer segment with RFM score >= 13 and high recency and frequency |
| **Churn** | When a customer stops purchasing/renewing subscriptions |
| **CLV (Customer Lifetime Value)** | Total revenue expected from a customer over their entire relationship |
| **Cohort** | Group of customers who signed up in the same time period |
| **Event** | A transaction record (order or invoice/renewal) |
| **Frequency Score** | 1-5 rating based on purchase count (higher = more purchases) |
| **High-Value Customer** | Customer with monetary score of 4 or 5 (spending $10,584+) |
| **Loyal Customer** | Customer with 2 or more purchases (repeat buyer) |
| **Monetary Score** | 1-5 rating based on total revenue (higher = more spending) |
| **Recency Score** | 1-5 rating based on days since last purchase (higher = more recent) |
| **Refund Rate** | Percentage of revenue that was refunded |
| **RFM** | Recency, Frequency, Monetary - customer segmentation framework |
| **RFM Total Score** | Sum of R + F + M scores, ranging from 3 to 15 |
| **Segment** | Group of customers with similar RFM characteristics |
| **Subscription** | Recurring purchase model (vs one-time purchase) |
| **Win-back Campaign** | Marketing effort to re-engage churned or at-risk customers |

### G. References & Resources

**RFM Analysis**:
- Bult, J. R., & Wansbeek, T. (1995). "Optimal Selection for Direct Mail." Marketing Science.
- Hughes, A. M. (1994). "Strategic Database Marketing." Probus Publishing.

**Customer Segmentation**:
- Wedel, M., & Kamakura, W. A. (2000). "Market Segmentation: Conceptual and Methodological Foundations."
- Kotler, P., & Keller, K. L. (2016). "Marketing Management" 15th Edition.

**Subscription Business Metrics**:
- Skok, D. "SaaS Metrics 2.0 – A Guide to Measuring and Improving What Matters." ForEntrepreneurs.
- Zuora. "Subscription Economy Index." Annual reports on subscription business trends.

---

## Summary

This documentation provides a complete reference for the e-commerce customer loyalty analysis project. It covers:

✅ **What**: Analysis of 4,000 loyal customers and 48,000 transactions
✅ **Why**: Identify loyal customers and channels that drive repeat purchases
✅ **How**: RFM scoring methodology with fixed ranges
✅ **Results**: 6 customer segments with actionable strategies
✅ **Tools**: Power Query (Cleaning and Transformation) → Python (RFM) → Power BI (Visualization)

### Key Takeaways

1. **All customers in this analysis are loyal** (2+ purchases minimum)
2. **RFM scoring uses fixed ranges** based on business context and data distribution
3. **Six segments identified**: Champions, High-Value Loyal, Loyal Frequent, Standard Loyal, At-Risk High-Value, At-Risk Standard
4. **Customer value varies widely**: $106 to $37,830 per customer
5. **Frequency is consistent**: Average 12 purchases, median 12 purchases
6. **Refunds are tracked but included** in calculations with negative impact

### Next Steps

1. **Review dashboard insights** with stakeholders
2. **Implement segment-specific strategies** (see Segmentation Strategy section)
3. **Set up monitoring** for key metrics (at-risk %, revenue at risk)
4. **Launch win-back campaigns** for at-risk high-value customers
5. **Optimize channel spending** based on segment acquisition patterns
6. **Schedule regular reviews** (monthly/quarterly) to track progress

---

**Document Version**: 3.0  
**Last Updated**: November 2025  
**Status**: Complete
