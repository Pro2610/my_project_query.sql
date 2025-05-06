# 📊 Monthly Campaign KPI Tracker with UTM Tags (Facebook & Google Ads)

## 🔍 Overview
This project builds a robust SQL-based solution to track campaign KPIs over time using paid traffic data from Facebook and Google Ads.  
It extracts campaign names from UTM tags and calculates monthly CTR, CPC, CPM, and ROMI, along with their **month-over-month percentage changes** using window functions.

## 🧰 Tools & Technologies
- SQL (BigQuery or PostgreSQL)
- Window functions: `LAG()`, `PARTITION BY`, `CASE`
- Campaign performance metrics
- Ad platforms: Facebook Ads, Google Ads

## 🎯 Business Goal
To monitor advertising efficiency on a monthly basis by campaign, spot trends, and support better decision-making based on dynamic changes in key metrics.

## 📈 Metrics Calculated
| Metric | Description |
|--------|-------------|
| **CTR** | Click-Through Rate = Clicks / Impressions × 100 |
| **CPC** | Cost Per Click = Spend / Clicks |
| **CPM** | Cost per 1,000 Impressions |
| **ROMI** | Return on Marketing Investment = Revenue / Spend |
| **Change %** | Month-over-month changes for CPM, CTR, and ROMI |

## 🧪 SQL Highlights
```sql
-- Month-over-month ROMI change
CASE 
  WHEN ROMI_utm IS NOT NULL AND ROMI_utm != 0 
  THEN ((ROMI - ROMI_utm) / ROMI_utm) * 100 
  ELSE NULL 
END AS ROMI_change
