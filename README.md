# hospitality-analysis
# Hotel Metrics Dashboard

This repository provides a comprehensive list of key metrics and their formulas for analyzing hotel performance. The metrics are grouped into categories such as Revenue, Capacity, Utilization, and more.

---

## Revenue and Bookings Metrics

### **Total Revenue**
Represents the total revenue realized from bookings.  
**Formula**:  
`Revenue = SUM(fact_bookings[revenue_realized])`

### **Total Bookings**
Total number of bookings that occurred.  
**Formula**:  
`Total Bookings = COUNT(fact_bookings[booking_id])`

### **Total Successful Bookings**
Total number of successful bookings across all hotels.  
**Formula**:  
`Total Successful Bookings = SUM(fact_aggregated_bookings[successful_bookings])`

### **Total Cancelled Bookings**
Total number of bookings that were canceled.  
**Formula**:  
`Total Cancelled Bookings = CALCULATE([TotalBookings], fact_bookings[booking_status]="Cancelled")`

---

## Performance and Ratios

### **Realization %**
Measures the percentage of successful bookings out of total bookings.  
**Formula**:  
`Realization % = 1 - ([Cancellation %] + [No Show Rate %])`

### **Cancellation Percentage**
Percentage of total bookings that were canceled.  
**Formula**:  
`Cancellation % = (Total Cancelled Bookings / Total Bookings) * 100`

### **Average Rating**
The average score customers provided in reviews.  
**Formula**:  
`Average Rating = AVERAGE(fact_bookings[ratings_given])`

---

## Capacity Metrics

### **Total Capacity**
The total number of rooms available across all hotels.  
**Formula**:  
`Total Capacity = SUM(fact_aggregated_bookings[capacity])`

### **SRN (Sellable Room Nights)**
The total number of rooms available to sell over a time period.  
**Formula**:  
`SRN = Total Capacity × Number of Days`

### **DSRN (Daily Sellable Room Nights)**
Average number of rooms available to sell per day.  
**Formula**:  
`DSRN = Total Capacity / Number of Days`

---

## Revenue Metrics

### **RevPAR (Revenue Per Available Room)**
Measures revenue per available room, accounting for all rooms.  
**Formula**:  
`RevPAR = Total Revenue / Total Capacity`

### **ADR (Average Daily Rate)**
Average revenue per booked room.  
**Formula**:  
`ADR = Total Revenue / Total Booked Rooms`

---

## Utilization Metrics

### **Occupancy %**
Percentage of available rooms that were successfully booked.  
**Formula**:  
`Occupancy % = (Total Successful Bookings / Total Capacity) * 100`

### **URN (Utilized Room Nights)**
Total number of rooms successfully used by customers.  
**Formula**:  
`URN = Total Checked Out Rooms`

### **BRN (Booked Room Nights)**
Total number of rooms booked (reserved), regardless of check-in.  
**Formula**:  
`BRN = Total Booked Rooms`

### **DURN (Daily Utilized Room Nights)**
Average number of utilized rooms per day.  
**Formula**:  
`DURN = Total Checked Out Rooms / Number of Days`

### **DBRN (Daily Booked Room Nights)**
Average number of booked rooms per day.  
**Formula**:  
`DBRN = Total Bookings / Number of Days`

---

## Timeframe Metrics

### **Number of Days**
Total days represented in the data.  
**Formula**:  
`Number of Days = DATEDIFF(MIN(dim_date[date]), MAX(dim_date[date]), DAY) + 1`

---

## Checked-Out Metrics

### **Total Checked-Out**
Total number of bookings marked as "Checked Out".  
**Formula**:  
`Total Checked Out = CALCULATE([TotalBookings], fact_bookings[booking_status]="Checked Out")`
