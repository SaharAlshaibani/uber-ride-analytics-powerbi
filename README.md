# Uber Ride Analytics (Power BI)

Compact Power BI report for analyzing ride bookings: trips, status mix, cancellations, revenue, ratings, ride duration, vehicle classes, and payment mix.

## 🔗 Live Report
**Open the interactive dashboard:**  
➡️ https://app.powerbi.com/view?r=eyJrIjoiNzI4NzQ1OTgtYzFjNy00ODNjLTg0MzEtNGQ0Zjc1ODAxZDgyIiwidCI6IjJkMzE5NGUzLTE2NTQtNDZiZC1iYWUyLWFkMzdiYTExYjBhZSIsImMiOjl9


## Data
- **Source file:** `./data/ncr_ride_bookings.csv`
- **Key fields:** Date, Time, Booking ID, Booking Status, Booking Value, Ride Distance,  
  Customer Rating, Driver Ratings, Payment Method, Vehicle Type/Class, Avg VTAT, Avg CTAT.

> PII is not included; dataset is for demo/analytics.

---

##  Report Pages
1. **Overview Look** – Trips by month, booking status classification, Cancelled Bookings KPI.  
2. **Performance & Operations** – Cancel reasons (customer/driver), **Cancellation Rate %**, peak hour/day.  
3. **Revenue Insights** – Distance by day, **Payment Mix** (UPI/Cash/Wallet/Card).  
4. **Vehicle & Rating Insights** – Avg booking value & Avg ride duration by vehicle class, Avg customer/driver ratings.

---

##  KPIs
- **Total Trips**, **Completed Trips**, **Cancelled Trips**, **Cancellation Rate %**  
- **Net Revenue** (Completed only), **AOV = Net Revenue / Completed Trips**  
- **Avg Ride Duration (min)** = `DATEDIFF(Avg VTAT, Avg CTAT, MINUTE)` with simple outlier rules  
- **Avg Customer Rating**, **Avg Driver Rating**

---

##  Method (Light DAX)
- Calculated column: **Ride Duration (min)** from VTAT→CTAT (ignore negative or >180 min).  
- Measure: **Avg Ride Duration (min)** via `AVERAGEX` on non-blank rows.  
- Normalized status → *Completed / Cancelled / No Driver Found / Incomplete*.  
- Cleaned **Payment Method** and **Vehicle Class** into concise buckets.  
- **Calendar** marked as Date table; 1→* relationship to fact `[Date]`.

Screen shots from the Dashboared:
<img width="1168" height="772" alt="image" src="https://github.com/user-attachments/assets/9838bd3d-757e-472c-ba61-b07fa920297b" />
<img width="1165" height="753" alt="image" src="https://github.com/user-attachments/assets/6488eca7-a667-48cf-a464-0768e4b4cda5" />
<img width="1148" height="752" alt="image" src="https://github.com/user-attachments/assets/110035a2-318e-4501-925b-90b62524350e" />
<img width="1144" height="742" alt="image" src="https://github.com/user-attachments/assets/9b9387c9-65eb-4a3f-9ac5-12a57cfa73f6" />



