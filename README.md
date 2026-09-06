# Airline Data Engineering Project

## About the Project

This project was completed as part of the NeoStats Data Engineer Intern assignment.

The aim of the project is to build a data pipeline using airline-related data from four datasets:

- Flights
- Bookings
- Payments
- Passengers

The data was first inspected to understand its structure and identify data-quality problems. It was then cleaned, transformed, validated, and combined into datasets that can be used for analysis and Power BI reporting.

---

## What I Worked On

The main steps in the project were:

1. Loaded the four datasets from the provided Excel workbook.
2. Checked the columns, data types, missing values, and duplicate records.
3. Cleaned the datasets and standardized important fields.
4. Handled missing and invalid values.
5. Derived airline names from flight ID prefixes where required.
6. Calculated flight duration using departure and arrival timestamps.
7. Identified overnight flights.
8. Compared calculated duration with the supplied duration to identify anomalies.
9. Checked relationships between bookings, flights, passengers, and payments.
10. Protected passenger information using hashing and masking.
11. Created an analytical dataset for reporting.
12. Created summary tables for the main KPIs.
13. Built a Power BI dashboard using the processed data.

---

## Airline Mapping

Airline names were derived from the flight ID where the airline value was missing or marked as unknown.

| Flight Prefix | Airline |
|---|---|
| SJ | SpiceJet |
| AI | Air India |
| UK | Vistara |
| 6F | IndiGo |

---

## Flight Duration

Flight duration was calculated using the departure and arrival timestamps.

```text
Flight Duration = Arrival Time - Departure Time
```
The calculated flight duration was converted into minutes for analysis.

Flights were also classified into two categories:

- Same Day
- Overnight

An overnight flight is defined as a flight where the arrival date is later than the departure date.

The calculated duration was compared with the duration supplied in the source data. A difference of more than 5 minutes was treated as a duration anomaly.

The duration anomaly field is not treated as an actual flight delay because the dataset does not contain separate scheduled and actual flight times.

---

## Data Quality Checks

Several data-quality checks were performed during the project, including:

- Missing airline values
- Duplicate flight records
- Missing payment amounts
- Invalid payment values
- Missing booking status
- Invalid booking status
- Missing passenger attributes
- Invalid flight IDs
- Flight duration inconsistencies
- Missing departure or arrival timestamps
- Referential integrity between the datasets

Validation checks were performed after the cleaning and transformation steps to identify any remaining data-quality issues.

---

## PII Protection

The passenger and booking datasets contain personally identifiable information (PII).

For the analytical data used for reporting, sensitive information was protected using the following methods:

- Passenger IDs were hashed using SHA-256
- Aadhaar IDs were masked
- Phone numbers were masked
- Email addresses were masked
- Sensitive passport and emergency-contact fields were removed from the BI dataset

The original raw dataset is not included in this public repository because it contains sensitive passenger information.

---

## Analytical Dataset

The main analytical dataset was created at the booking level.

It combines information from:

- Bookings
- Flights
- Payments
- Protected passenger information

Some of the fields available for analysis include:

- Booking ID
- Flight ID
- Airline
- Source
- Destination
- Booking Date
- Booking Status
- Departure Time
- Arrival Time
- Flight Duration
- Flight Day Type
- Duration Status
- Payment Amount
- Payment Method
- Protected passenger information

The analytical dataset is structured to support reporting and analysis in Power BI while avoiding exposure of raw sensitive passenger information.

---

## KPIs

The project includes the following main KPIs and analytical metrics:

- Total Bookings
- Total Flights
- Average Flight Duration
- Total Payment
- Duration Anomalies
- Overnight Flights
- Airline-wise Bookings
- Route-wise Traffic
- Booking Status Distribution
- Monthly Booking Trends

These metrics are used to provide an overall view of bookings, flights, airline distribution, route performance, payment information, and flight-duration quality.

---

## Power BI Dashboard

The Power BI report contains three pages.

### 1. Executive Overview

This page provides an overall view of the airline data.

It includes:

- Total Bookings
- Total Flights
- Average Flight Duration
- Total Payment
- Duration Anomalies
- Bookings by Airline
- Booking Status
- Monthly Booking Trend

This page is designed to provide a quick summary of the main business and operational metrics.

### 2. Flight Duration & Anomalies

This page focuses on flight duration analysis and duration-related data-quality issues.

It includes:

- Average Flight Duration
- Overnight Flights
- Duration Anomalies
- Average Duration by Airline
- Same-Day vs Overnight Flights
- Duration Validation Status
- Flight Duration Distribution

This page helps identify flight-duration patterns, overnight flights, and differences between the calculated and supplied duration values.

### 3. Route Performance

This page focuses on route-level analysis.

It includes:

- Top Routes by Traffic
- Average Duration by Route
- Route Duration Anomalies
- Route-level Details
- Source and Destination Analysis

This page helps compare traffic and flight-duration patterns across different routes.
