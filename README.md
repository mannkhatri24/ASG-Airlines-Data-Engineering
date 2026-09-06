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
