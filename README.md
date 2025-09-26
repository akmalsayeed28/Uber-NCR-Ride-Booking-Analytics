# Uber Rides Data Analysis and Insights

This repository contains the workflow, analysis, and actionable insights derived from the Uber rides dataset in NCR. The analysis covers data cleaning, transformation, operational metrics, ride demand patterns, customer behavior, and revenue insights.

---

## 1. Data Cleaning and Transformation

Here’s how I approached preparing the dataset for analysis:

### Loading and Exploring the Data
- Imported core Python libraries: `pandas`, `numpy`, `seaborn`, `matplotlib`.
- Loaded the dataset using `pd.read_csv()` and inspected it with `df.head()` and `df.info()`.
- Identified missing values using `df.isnull().sum()`.

### Handling Missing Data
- Missing values were found in `Avg VTAT`, `Avg CTAT`, `Booking Value`, ratings, and reason columns.
- Created a unified indicator `reasonmissingflag` to mark rows with absent cancellation or incomplete reasons.
- Filled missing reasons for incomplete/cancelled rides with `"Unknown"` or `"Not Applicable"` depending on context.

### Consolidating Cancellation and Incomplete Reasons
- Multiple columns tracked reasons for cancellations/incompletions.
- Wrote a custom function `choose_reason()` and applied it with `df.apply()` to create a single column `IncompleteRideReasonClean`.

### Streamlining Columns and Naming
- Dropped redundant columns and intermediate flags with `df.drop()`.
- Re-labeled columns for clarity, including mapping binary ride status to `RideStatus` with `"Complete"` or `"Incomplete"`.

### Feature Engineering for Datetime and Categorical Variables
- Standardized date and time columns with `pd.to_datetime()`.
- Extracted features like booking hour and day of week.
- Created time-of-day bins (morning, afternoon, evening, night).
- Standardized categorical variables for vehicle type and reasons.

### Analysis, Aggregation, and Export
- Used `groupby`, `value_counts`, and summary statistics for aggregation.
- Visualized distributions, reasons, turnaround time, and distance metrics using `seaborn` and `matplotlib`.
- Exported cleaned, analytics-ready dataset to CSV for reporting and dashboarding.

### Key Methods and Functions
- Data exploration: `pd.read_csv()`, `df.head()`, `df.info()`, `df.isnull().sum()`
- Column operations: `df.drop()`, `df.rename()`
- Custom functions: `choose_reason()` with `df.apply()`
- Feature engineering: `pd.to_datetime()`, `.unique()`, `.replace()`
- Aggregation: `groupby()`, `value_counts()`
- Visualization: `seaborn`, `matplotlib`
- Export: `df.to_csv()`

---

## 2. Loading Cleaned Data into Power BI
- After cleaning and transforming the dataset, I exported it to a new CSV file.
- Loaded the cleaned CSV into **Power BI** for further analysis, aggregation, and interactive dashboarding.
- This allowed for visual exploration of trends, ride demand patterns, cancellations, operational efficiency, and customer behavior.

---

## 3. Ride Demand and Booking Patterns

![Power BI Dashboard](Screenshot_2025-09-27_003622.png)

**Findings:**
- Total annual bookings: 150,000.
- Monthly demand stable at ~13,000 rides/month; minor fluctuations.
- Autos and Go Mini are most booked, particularly in Jasola and Panchsheel Park.
- Ride requests show hourly spikes at peak locations.

**Actionable Insights:**
- Demand is concentrated in specific vehicle types and locations.
- Regular peaks can be leveraged for dynamic resource allocation.

**Recommendations:**
- Shift more supply (drivers) to high-demand zones during peak hours with geo-targeted prompts and incentives.
- Promote underutilized vehicle types in low-demand areas using discounted fares or vouchers.

---

## 4. Ride Completion, Cancellations, and Drop-offs

**Findings:**
- Completion rate: 62%; 38% cancelled or incomplete.
- Top cancellation reasons: no driver found, customer issues, vehicle breakdown, wrong address, change of plan.
- Lost revenue is significant due to incomplete rides.
- Average incomplete ride: 10.55 km, 20 minutes.

**Actionable Insights:**
- “No driver found” is the largest controllable cause of incomplete rides.
- Customer/system-related cancellations highlight opportunities for improved app experience.

**Recommendations:**
- Refine matching algorithms for faster driver assignment during peak times.
- Run preventive fleet maintenance.
- Implement proactive notifications for ride delays/cancellations.
- Educate drivers/customers about accurate addresses and minimizing frivolous cancellations.

---

## 5. Operational Efficiency Metrics

**Findings:**
- Average Turnaround Time (VTAT) fastest for completed rides, slowest for cancelled/incomplete.
- Average ride duration: 30.03 minutes for completed rides.
- Driver reach time: 8–10 minutes consistently.

**Actionable Insights:**
- Cancellations increase idle time, reducing productive rides per driver.
- Potential to optimize routes, minimize idle time, and maximize utilization.

**Recommendations:**
- Predictive analytics for driver shift planning based on demand/cancellation history.
- Launch “on-trip support” features for drivers.
- Incentivize completion of longer, higher-value trips.

---

## 6. Customer Behavior and Revenue

**Findings:**
- Repeat customers contribute disproportionately to revenue.
- Payment preferences: Cash, UPI, Uber Wallet; digital adoption partial.
- Ratings: Customers 4.40/5, drivers 4.23/5; generally positive.

**Actionable Insights:**
- Loyalty among high-value customers is key for sustainable growth.
- Payment friction persists for some segments.

**Recommendations:**
- Launch loyalty/reward programs for repeat/high-value customers.
- Optimize in-app payment UX and promote wallet/UPI adoption via cashback/partner offers.
- Target communication/promotions to high-repeat customers for retention.

---

## 7. Summary

Throughout this workflow, I focused on:
- Robust handling of missing values.
- Consolidation of reason fields.
- Effective feature engineering.
- Standardization of categorical data.
- Visual analytics for actionable insights.

This process prepared the Uber rides dataset for **deep-dive reporting**, **Power BI dashboarding**, and **actionable business insights**.
