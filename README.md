# 🏨 Hotel Booking Demand — Data Analysis & Dashboard


> An end-to-end Excel project covering data cleaning, exploratory data analysis, and a dashboard built on the Hotel Booking Demand dataset.

---

## 📌 Project Overview

This project analyzes hotel booking data from two hotel types — a **City Hotel** and a **Resort Hotel** — covering the period from **2015 to 2017**. The goal was to uncover patterns in bookings, cancellations, revenue, and guest behavior to support data-driven business decisions.

The project demonstrates a complete data analytics workflow entirely within Microsoft Excel:
- Raw data ingestion and inspection
- Data cleaning and preprocessing
- Exploratory data analysis using Pivot Tables
- A dashboard with charts and KPI cards

---

## 📂 Repository Structure

```
hotel-booking-analysis/
│
├── hotel_bookings_raw.csv          # Original unmodified dataset
├── hotel_bookings_analysis.xlsx    # Cleaned data, analysis & dashboard
├── dashboard_preview.png           # Screenshot of the final dashboard
└── README.md                       # Project documentation
```

---

## 🗂️ Dataset

| Property | Details |
|---|---|
| **Source** | [Kaggle — Hotel Booking Demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand) |
| **Original Size** | 119,390 rows × 32 columns |
| **Period** | July 2015 — August 2017 |
| **Hotel Types** | City Hotel, Resort Hotel |
| **License** | CC0: Public Domain |

---
## 📥 Download
The full Excel workbook (cleaned data + analysis + dashboard) is available here:
[Download Excel File](https://docs.google.com/spreadsheets/d/113BNQRvJYz_kpglou2EFPM4TnHih_Zu1/edit?usp=drive_link&ouid=109679100370012780952&rtpof=true&sd=true)

---
## 🧹 Data Cleaning & Preprocessing

All cleaning was performed in Excel and documented in a dedicated sheet. The following issues were identified and resolved:

### Missing Values
| Column | Null % | Action |
|---|---|---|
| `company` | 94.31% | Dropped column entirely |
| `agent` | 13.69% | Filled with 0 (no agent) |
| `country` | 0.41% | Filled with "Unknown" |
| `children` | 0.003% | Filled with 0 (no children) |

### Data Quality Issues
- **Duplicate rows** — Identified and removed using Excel's Remove Duplicates on all columns
- **Zero-guest bookings** — Removed ~180 rows where `adults = 0`, `children = 0`, and `babies = 0` simultaneously (logically invalid)
- **Negative ADR values** — Removed rows with `adr < 0` (invalid revenue entries)
- **ADR outliers** — Identified and removed extreme outlier values in the `adr` column to ensure accurate revenue analysis
- **"Undefined" meal values** — Replaced with "SC" (no meal package) using Find & Replace


### Feature Engineering
New columns created to support analysis:

| New Column | Formula Logic |
|---|---|
| `arrival_date` | Combined `year`, `month`, `day` columns into a single date |
| `total_stays` | `stays_in_weekend_nights + stays_in_week_nights` |
| `total_guests` | `adults + children + babies` |
| `revenue` | `adr × total_stays` |
| `lead_time_category` | Bucketed `lead_time` into Short (≤30), Medium (31–90), Long (90+) days |

---

## 📊 Analysis & Key Insights

### 🏨 Hotel Performance
- City Hotel accounts for **61%** of total bookings (53,271) vs Resort Hotel (33,950)
- City Hotel has a higher cancellation rate (**30%**) compared to Resort Hotel (**23%**)

### 🔁 Cancellation Analysis
- **38%** of all bookings were cancelled (24,008 out of 87,221)
- Lead time has a strong impact on cancellations — short bookings (0–30 days) cancel at only **16%** vs long bookings (90+ days) at **37%**
- Counterintuitively, **Non-Refund deposit type** has the highest cancellation rate at **95%**
- **Online TA** is the largest market segment (51,550 bookings) and accounts for the most cancellations (18,242) at a **35%** rate
- **Corporate** segment is the most reliable with only a **12%** cancellation rate
- **Transient** customers account for the majority of cancellations (21,660) at a **30%** rate
- **Group** customer type is the most reliable with only a **10%** cancellation rate

### 📅 Booking Trends
- **August** is the peak month with **11,242 bookings**, while **January** is the slowest with only **4,685**
- Cancellation rate peaks in **July and August (~32%)** even during the busiest period
- **2016** recorded the highest bookings (42,309) — note that 2015 and 2017 are partial years and should not be directly compared
- November has the lowest cancellation rate of the year at **21%**

### 💰 Revenue Analysis
- ADR follows a clear seasonal pattern — lowest in **January ($70)** and highest in **August ($151)**, more than double
- **Room type A** generates the highest total revenue (**$17.4M**) driven by volume despite having a relatively low ADR ($92)
- **Room type H** commands the highest ADR ($189) but contributes minimal revenue due to low booking volume
- Total revenue across all bookings reached **$34.4M**

### 👥 Guest Analysis
- **Portugal (PRT)** dominates with 27,350 bookings (**35%** of total), followed by UK (10,422), France (8,823), Spain (7,244), and Germany (5,385)
- Only **3.9%** of guests are repeat visitors (3,363 out of 87,221)
- Repeat guests cancel at only **8%** compared to **28%** for new guests — making them **3.5x less likely to cancel**
- Retaining existing guests is significantly more reliable than acquiring new ones

---

## 📈 Dashboard

The dashboard was built in Excel using Pivot Charts, presenting a clear visual summary of the most important findings across all analysis areas.

### KPI Cards
- Total Bookings
- Cancellation Rate
- Average ADR

### Visualizations
- **Booking vs Cancellation over Months** 
- **Booking vs Cancellation by Hotel Type** 
- **Booking vs Cancellation by Lead Duration** 
- **ADR Average by Month** 
- **Total Bookings by Country** 
- **Bookings by Customer Type** 
- **Revenue vs ADR by Room Type** type

> 📸 *See `dashboard_preview.png` for a full screenshot of the dashboard*

---

## 🛠️ Tools Used

- **Microsoft Excel** — Data cleaning, Pivot Tables, Charts, Dashboard, Slicers



