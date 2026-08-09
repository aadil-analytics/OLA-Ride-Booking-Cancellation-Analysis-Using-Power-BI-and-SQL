# 🚕 OLA Ride Booking & Cancellation Analysis

## 📌 Project Overview

This project analyzes **103,024 OLA ride booking records** for July 2024 using **SQL and Power BI**.

The objective is to understand booking performance, cancellation behavior, revenue, vehicle-type performance, payment methods, ride distance, and customer/driver ratings, and to convert the analysis into actionable business insights.

The project combines:

- **SQL** → Business-question-driven data analysis
- **Power BI** → Interactive dashboards and visual storytelling
- **Excel** → Source/raw dataset

---

## 🎯 Business Objectives

The analysis focuses on answering questions such as:

- How many bookings were successful, cancelled, or unsuccessful?
- What is the overall cancellation rate?
- What are the major reasons for customer and driver cancellations?
- Which vehicle types generate the most booking value?
- What is the average ride distance for each vehicle type?
- Which payment methods contribute the most revenue?
- Which customers have the highest number of bookings?
- How do customer and driver ratings vary across vehicle types?
- What is the value of successfully completed rides?
- What are the major reasons for incomplete rides?

---

# 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **SQL / MySQL** | Data analysis and business questions |
| **Power BI** | Interactive dashboards and visualization |
| **Power Query** | Data cleaning and transformation |
| **DAX** | Measures and KPI calculations |
| **Excel** | Raw dataset |

---

# 📂 Project Structure

```text
OLA-Ride-Booking-Analysis/
│
├── data/
│   └── Bookings-100000-Rows.xlsx
│
├── sql/
│   └── ola sql project.sql
│
├── powerbi/
│   └── OLA_Ride_Analysis.pbix
│
├── dashboard/
│   ├── Overall Dashboard.png
│   ├── Rating Dashboard.png
│   ├── Revenue Dashboard.png
│   ├── Vehicle Type Dashboard.png
│   └── Cancellation Dashboard.png
│
└── README.md
```

> File/folder names can be adjusted to match the final GitHub repository structure.

---

# 📊 Dataset Overview

The dataset contains **103,024 booking records** and includes fields related to:

- Booking date and time
- Booking ID
- Booking status
- Customer ID
- Vehicle type
- Pickup and drop locations
- Booking value
- Payment method
- Ride distance
- Driver ratings
- Customer ratings
- Customer cancellation reasons
- Driver cancellation reasons
- Incomplete ride information

### Main Booking Statuses

| Booking Status | Count |
|---|---:|
| Success | 63,967 |
| Canceled by Driver | 18,434 |
| Canceled by Customer | 10,499 |
| Driver Not Found | 10,124 |
| **Total** | **103,024** |

---

# 🧮 Key KPIs

### Total Bookings
**103,024**

### Successful Bookings
**63,967**

### Successful Booking Rate
**62.09%**

### Customer Cancellations
**10,499**

### Driver Cancellations
**18,434**

### Driver Not Found
**10,124**

### Overall Cancellation Rate
**28.08%**

### Total Booking Value
Approximately **₹56.53M**

### Successful Booking Value
Approximately **₹35.08M**

---

# 📈 Power BI Dashboard

The Power BI report contains **5 interactive dashboard pages**.

## 1. Overall Dashboard

Provides a high-level view of:

- Total bookings
- Total booking value
- Booking status breakdown
- Ride volume over time
- Date-based filtering

![Overall Dashboard](dashboard/Overall%20Dashboard.png)

---

## 2. Ratings Dashboard

Analyzes:

- Driver ratings by vehicle type
- Customer ratings by vehicle type
- Comparison of ratings across different vehicle categories

![Ratings Dashboard](dashboard/Rating%20Dashboard.png)

---

## 3. Revenue Dashboard

Analyzes:

- Revenue by payment method
- Ride distance trends
- Top customers
- Booking value distribution

![Revenue Dashboard](dashboard/Revenue%20Dashboard.png)

---

## 4. Vehicle Type Dashboard

Compares vehicle categories based on:

- Total booking value
- Successful booking value
- Average distance travelled
- Total distance travelled

![Vehicle Type Dashboard](dashboard/Vehicle%20Type%20Dashboard.png)

---

## 5. Cancellation Dashboard

Focuses on cancellation behavior:

- Total bookings
- Successful bookings
- Cancelled bookings
- Cancellation rate
- Customer cancellation reasons
- Driver cancellation reasons

![Cancellation Dashboard](dashboard/Cancellation%20dashboard.png)

---

# 🔍 Key Insights

### 1. Booking Success & Cancellation

Out of **103,024 bookings**, **63,967 were successful**, resulting in a successful booking rate of approximately **62.09%**.

The combined customer and driver cancellation rate is approximately **28.08%**.

---

### 2. Driver Cancellations Are a Major Issue

Driver cancellations (**18,434**) are significantly higher than customer cancellations (**10,499**).

This indicates that reducing driver-side cancellations could be an important operational priority.

---

### 3. Customer Cancellation Reasons

The major customer cancellation reasons include:

| Reason | Count |
|---|---:|
| Driver is not moving towards pickup location | 3,175 |
| Driver asked to cancel | 2,670 |
| Change of plans | 2,081 |
| AC is not working | 1,568 |
| Wrong address | 1,005 |

The largest customer-side issue is the **driver not moving toward the pickup location**, suggesting a potential driver allocation or driver behavior problem.

---

### 4. Driver Cancellation Reasons

Major driver cancellation reasons include:

| Reason | Count |
|---|---:|
| Personal & car related issue | 6,542 |
| Customer related issue | 5,413 |
| Customer was coughing/sick | 3,654 |
| More than permitted people | 2,825 |

**Personal and car-related issues** are the largest driver cancellation category.

---

### 5. Payment Method

Based on booking value, **Cash** contributes the highest revenue, followed by **UPI**.

Approximate booking value:

- Cash → **₹19.26M**
- UPI → **₹14.17M**
- Credit Card → **₹1.31M**
- Debit Card → **₹0.34M**

---

### 6. Vehicle Type & Ride Distance

The **Prime Sedan** has one of the highest average ride distances at approximately **15.76 km**.

The **Auto** category has a much lower average ride distance at approximately **6.24 km**, indicating a substantially different usage pattern compared with the other vehicle categories.

---

### 7. Ratings

Average customer and driver ratings remain close to **4.0 across vehicle categories**, suggesting relatively consistent service ratings across the fleet.

---

# 🧑‍💻 SQL Analysis

The SQL analysis contains business questions covering:

1. Retrieve all successful bookings
2. Find average ride distance for each vehicle type
3. Calculate total customer-cancelled rides
4. Identify the top 5 customers by number of rides
5. Find driver cancellations due to personal/car-related issues
6. Find maximum and minimum driver ratings for Prime Sedan
7. Retrieve rides paid using UPI
8. Calculate average customer rating by vehicle type
9. Calculate total booking value of successful rides
10. Retrieve incomplete rides and their reasons

The SQL file uses **views** to organize the analysis and then queries those views to retrieve the results.

---

# 📌 Example SQL Analysis

### Average Ride Distance by Vehicle Type

```sql
SELECT
    Vehicle_Type,
    AVG(Ride_Distance) AS avg_distance
FROM bookings
GROUP BY Vehicle_Type;
```

### Successful Booking Value

```sql
SELECT
    SUM(Booking_Value) AS total_successful_ride_value
FROM bookings
WHERE Booking_Status = 'Success';
```

### Average Customer Rating by Vehicle Type

```sql
SELECT
    Vehicle_Type,
    AVG(Customer_Rating) AS avg_customer_rating
FROM bookings
GROUP BY Vehicle_Type;
```

---

# 📊 Power BI Techniques Used

### Data Preparation
- Data cleaning using Power Query
- Handling missing values
- Data type formatting
- Date and time preparation

### DAX
Created measures for KPIs such as:

- Total Bookings
- Successful Bookings
- Cancelled Bookings
- Cancellation Rate
- Total Booking Value
- Successful Booking Value
- Average Ratings

### Visualization
Used:

- KPI Cards
- Donut/Pie Charts
- Bar Charts
- Column Charts
- Line Charts
- Tables
- Slicers
- Date Range Filters
- Interactive navigation

---

# 💡 Business Recommendations

Based on the analysis, the following actions could help improve operational performance:

### 1. Reduce Driver Cancellations
Investigate personal/car-related issues and improve driver support, vehicle maintenance, and driver policies.

### 2. Improve Driver Allocation
The high number of customer cancellations related to drivers not moving toward pickup suggests that driver assignment and pickup adherence should be monitored.

### 3. Improve Driver Experience
Since driver cancellations exceed customer cancellations, understanding driver-side operational pain points could have a meaningful impact on overall booking success.

### 4. Monitor Vehicle Performance
Vehicle-level analysis of booking value, distance, and ratings can help identify categories requiring operational attention.

### 5. Improve Customer Experience
Cancellation reasons such as driver behavior, vehicle issues, and service problems can be used to identify areas where customer experience can be improved.

---

# 🚀 Project Outcome

This project demonstrates an end-to-end **Data Analyst workflow**:

```text
Raw Data
   ↓
Data Cleaning
   ↓
SQL Analysis
   ↓
Business Questions
   ↓
DAX Measures
   ↓
Power BI Dashboards
   ↓
Insights
   ↓
Business Recommendations
```

The project focuses not only on creating visualizations but also on translating raw ride-booking data into **business-relevant insights and recommendations**.

---

# 👨‍💻 Skills Demonstrated

- SQL
- MySQL
- Power BI
- DAX
- Power Query
- Data Cleaning
- Exploratory Data Analysis
- KPI Development
- Data Visualization
- Business Analysis
- Dashboard Design
- Insight Generation

---

## ⭐ Author

**Aadil**

Data Analytics Project | SQL + Power BI
