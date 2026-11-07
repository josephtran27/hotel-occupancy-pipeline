Hotel Occupancy & Revenue Forecasting Pipeline

Overview
This repository contains a Python-based data pipeline designed to ingest On-The-Books (OTB) reservation data and local event schedules to generate a 90-day rules-based forecast. The model predicts daily occupancy, total room demand, and projected revenue for properties in high-volatility markets (Boston, MA and Santa Monica, CA), providing actionable data for revenue management and dynamic pricing strategies.

Business Value
Hospitality revenue optimization requires balancing historical booking curves with forward-looking market anomalies. Rather than relying on rigid historical averages, this pipeline utilizes a customized architecture to proactively adjust for massive local demand shocks, ensuring accurate capacity and revenue projections even during extreme market compression. This demonstrates the foundational data wrangling required before tabular business data is fed into advanced machine learning models.

Key Features & Methodology
Event-Driven Demand Modeling: Engineered features to isolate and dynamically adjust occupancy caps for major localized demand shocks, such as the Boston Marathon pushing capacity to near 100% and the Venice Love Fest.

OTB Booking Curve Analysis: Processes raw reservation data to calculate lead time days, day-of-week booking velocity, and baseline pickup rates.

Defensive Cancellation Filtering: Implements rules-based logic to account for booking fallout and capacity adjustments within the lead-time window.

Automated Data Consolidation: Merges disparate data-otb.csv and data-events.csv feeds into a single, clean 90_day_forecast_clean.csv output ready for business intelligence dashboards.

Technical Stack
Language: Python 3.13

Libraries: Pandas (Data manipulation, time-series grouping, and feature engineering)

Environment: Compatible with macOS, utilizing standard virtual environments (e.g., uv).

Repository Structure
Plaintext
├── 90_day_forecast.py          # Core forecasting script and pipeline logic
├── data-events.csv             # Local market events and demand shock indicators
├── data-otb.csv                # Raw On-The-Books reservation data
├── 90_day_forecast_clean.csv   # Target pipeline output (Forecasted metrics)
├── hotel_analysis.ipynb        # Exploratory data analysis and methodology validation
└── README.md
How to Run
Clone the repository to your local machine.

Ensure you have Python and Pandas installed.

Run the primary script via the terminal:

Bash
python 90_day_forecast.py
The script will process the raw CSVs and output the final projections to 90_day_forecast_clean.csv.