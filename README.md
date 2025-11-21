# 🚚 Amazon Last-Mile Delivery Analytics Dashboard (Power BI)

## 📌 Project Overview
This project analyzes Amazon’s last-mile delivery performance using a complete Power BI analytics workflow — from raw data cleaning to building a multi-page interactive dashboard.  
The goal is to identify delivery bottlenecks, operational inefficiencies, and data quality issues while showcasing strong data modeling, DAX, and visualization skills.

The final dashboard includes:
- **Executive Overview**
- **Delivery Performance**
- **Late Delivery Analysis**
- **Operational Insights**
- **Executive Summary (Insights + Recommendations)**

---

## 📊 Dataset
- **Source:** Kaggle – Amazon Delivery dataset  
- **Tool Used:** Power BI (Power Query + Power BI Desktop)

### Key Steps Performed
- Removed duplicate records  
- Handled null values  
- Corrected inconsistent column names and formats  

---

## ❓ Key Business Questions Answered
1. How many deliveries are completed on time vs late?  
2. Which areas, traffic levels, and weather conditions cause the most delays?  
3. Where can operational improvements be made?  
4. Which product categories and delivery vehicles handle the highest volume?  
5. How many records contain missing weather/traffic data or invalid store locations?  
6. Are any deliveries handled by under-age agents?

---

## 🧹 Data Cleaning & Preparation
Performed using **Power Query** and **Power BI**, including:

- Removed duplicates, handled null values, corrected data types, and standardized date/time formats  
- Converted text-based columns into proper **Date/Time**, **Whole Number**, or **Decimal** types  
- Created custom columns, such as:
  - **Order–Pickup Time Comparison**  
  - **Age_Status** (under-age agent detection)  
  - **Store Location Status** (valid vs invalid GPS coordinates)  
  - **Drop Location Status**  
  - **Delivery Status** (On-Time vs Late)  
  - **Delivery Time Bins** (0–20, 20–40, … 260–280 minutes)  
- Built key DAX measures, such as:
  - **Average Delivery Time**  
  - **Total Orders**  
  - **Average Agent Age**  
  - **Late Deliveries %**  
  - **On-Time Deliveries %**  
  - **Missing Weather Records**  
  - **Missing Traffic Records**

---

## 🧮 Example DAX Measures

```DAX
Missing Weather Records =
COUNTROWS(
    FILTER(
        'amazon_delivery',
        'amazon_delivery'[Weather] = "null"
    )
)

Invalid Time Records =
COUNTROWS(
    FILTER(
        'amazon_delivery',
        'amazon_delivery'[Order-Pickup Time Comparison] <> "Valid"
    )
)

Average Delivery Time =
AVERAGE('amazon_delivery'[Delivery_Time in minutes])

On Time Deliveries % =
DIVIDE([On Time Deliveries], [Total Orders])
