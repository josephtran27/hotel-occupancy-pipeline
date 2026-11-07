# 🏨 Hotel Occupancy & Revenue Forecasting Pipeline

A Python-based forecasting pipeline that integrates **On-The-Books (OTB) reservation data**, local event schedules, and rules-based demand modeling to generate actionable **90-day hotel occupancy and revenue forecasts**.

Designed for high-volatility hospitality markets, including **Boston, MA** and **Santa Monica, CA**, the pipeline transforms raw operational data into structured projections that support revenue management, capacity planning, and dynamic pricing decisions.

---

## 📖 Overview

Hotel demand is influenced by more than historical booking patterns. Seasonal fluctuations, reservation cancellations, booking lead times, and major local events can significantly impact occupancy and revenue performance.

This project addresses those challenges through an automated data processing and forecasting workflow that:

- Analyzes existing reservations and booking lead times.
- Estimates daily occupancy and anticipated room demand.
- Incorporates event-driven demand adjustments.
- Accounts for cancellations and booking pickup behavior.
- Generates a consolidated 90-day forecast dataset.

The resulting output provides a structured foundation for hospitality analytics, revenue optimization, and future machine learning applications.

---

## 💼 Business Value

Traditional forecasting approaches that rely heavily on historical averages may struggle to capture sudden changes in local market demand.

This pipeline introduces **event-aware, rules-based forecasting** to better account for demand volatility and localized market compression.

### Key Business Applications

- **Revenue Optimization:** Support pricing decisions with forward-looking occupancy and revenue estimates.
- **Demand Forecasting:** Identify periods of elevated demand driven by local events and booking activity.
- **Capacity Planning:** Estimate room utilization and potential occupancy constraints.
- **Operational Efficiency:** Automate the transformation of raw booking data into standardized forecasting outputs.
- **Machine Learning Readiness:** Establish a clean, feature-engineered dataset suitable for future predictive modeling.

---

## ⚙️ Key Features & Methodology

### 1. Event-Driven Demand Modeling

Integrates local event schedules to identify potential demand shocks that may significantly influence hotel occupancy.

**Examples include:**
- **Boston Marathon:** Models heightened demand and potential near-capacity occupancy during a major citywide event.
- **Venice Love Fest:** Incorporates localized event-driven demand changes in the Santa Monica market.

Event-specific adjustments are applied to baseline demand estimates while respecting hotel capacity constraints.

### 2. On-The-Books (OTB) Booking Curve Analysis

Processes reservation data to evaluate booking activity and estimate future demand.

**Engineered forecasting features include:**
- Reservation lead time in days.
- Day-of-week booking patterns.
- Baseline booking pickup rates.
- Booking velocity and occupancy trends.

These features help establish the underlying demand trajectory across the forecast horizon.

### 3. Defensive Cancellation Filtering

Implements rules-based adjustments to account for reservation cancellations and expected booking fallout.

This helps prevent projections from relying exclusively on existing reservations without considering potential changes before arrival.

### 4. Automated Data Consolidation

Combines reservation and event datasets into a unified forecasting output.

**Input datasets:**
- `data-otb.csv` — On-The-Books reservation data.
- `data-events.csv` — Local events and demand indicators.

**Generated output:**
- `90_day_forecast_clean.csv` — Consolidated 90-day forecast dataset.

The final output is structured for downstream analysis and integration with business intelligence dashboards.

---

## 🛠️ Technical Stack

| Component | Technology | Purpose |
|---|---|---|
| Programming Language | Python 3.13 | Core pipeline development |
| Data Processing | Pandas | Data cleaning, aggregation, and transformations |
| Feature Engineering | Pandas | Booking curves, lead times, and event adjustments |
| Forecasting | Rules-Based Modeling | Occupancy and revenue projections |
| Data Storage | CSV | Input datasets and forecast outputs |
| Exploratory Analysis | Jupyter Notebook | Data exploration and methodology validation |
| Development Environment | macOS / Python Virtual Environment | Local development and execution |

---

## 📂 Repository Structure

```text
Hotel-Occupancy-Forecasting/
│
├── 90_day_forecast.py          # Core forecasting pipeline
├── data-events.csv             # Local events and demand indicators
├── data-otb.csv                # On-The-Books reservation data
├── 90_day_forecast_clean.csv   # Generated 90-day forecast
├── hotel_analysis.ipynb        # Exploratory analysis and validation
└── README.md                   # Project documentation
```

---

## 🔄 Pipeline Architecture

The forecasting workflow follows four primary stages:

```text
        ┌───────────────────────┐
        │    Raw Data Sources   │
        └───────────┬───────────┘
                    │
          ┌─────────┴─────────┐
          │                   │
          ▼                   ▼
   ┌──────────────┐   ┌──────────────┐
   │ OTB Bookings │   │ Local Events │
   │  (CSV Data)  │   │  (CSV Data)  │
   └──────┬───────┘   └──────┬───────┘
          │                  │
          └─────────┬────────┘
                    ▼
          ┌──────────────────┐
          │ Data Cleaning &  │
          │ Feature Creation │
          └────────┬─────────┘
                   ▼
          ┌──────────────────┐
          │ Rules-Based      │
          │ Forecast Engine  │
          └────────┬─────────┘
                   ▼
          ┌──────────────────┐
          │ 90-Day Occupancy │
          │ & Revenue Output │
          └────────┬─────────┘
                   ▼
       90_day_forecast_clean.csv
```

### Forecasting Workflow

1. **Data Ingestion:** Load reservation and local event CSV datasets.
2. **Data Preparation:** Clean and consolidate booking and event information.
3. **Feature Engineering:** Calculate lead times, booking patterns, and event indicators.
4. **Demand Adjustments:** Apply booking pickup, cancellation, and event-based rules.
5. **Forecast Generation:** Estimate daily occupancy, room demand, and projected revenue.
6. **Data Export:** Save the consolidated 90-day forecast as a clean CSV dataset.

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed:

- Python 3.13
- Pandas
- A Python-compatible terminal or development environment

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd Hotel-Occupancy-Forecasting
```

Replace `<your-repository-url>` with your actual GitHub repository URL.

### 2. Install Dependencies

```bash
python -m pip install pandas
```

### 3. Run the Forecasting Pipeline

```bash
python 90_day_forecast.py
```

### 4. Review the Output

After execution, the pipeline generates:

```text
90_day_forecast_clean.csv
```

This file contains the consolidated forecasting results for downstream analysis and reporting.

---

## 📊 Forecasting Outputs

The pipeline is designed to produce daily projections across a **90-day forecast horizon**.

| Forecast Metric | Description |
|---|---|
| Forecast Date | Date associated with each projection |
| Projected Occupancy | Estimated percentage of available rooms occupied |
| Expected Room Demand | Estimated number of rooms demanded |
| Projected Revenue | Estimated room revenue based on forecast demand |
| Event Impact | Demand adjustments associated with local events |
| Booking Pickup | Expected additional reservations before arrival |

These metrics can support revenue management reporting, occupancy monitoring, and future predictive analytics workflows.

---

## 🔮 Future Enhancements

Potential extensions include:

- **Machine Learning Forecasting:** Introduce predictive models to complement the existing rules-based approach.
- **Model Evaluation:** Compare forecast results against actual occupancy and revenue performance.
- **Interactive Dashboards:** Visualize occupancy trends and demand fluctuations through Power BI or Streamlit.
- **Automated Data Ingestion:** Replace static CSV inputs with scheduled data feeds or APIs.
- **Advanced Pricing Optimization:** Incorporate ADR and RevPAR analysis into forecasting and pricing recommendations.

---

## 🎯 Project Takeaways

This project demonstrates practical experience in:

- Building an end-to-end Python data processing pipeline.
- Transforming raw reservation data into forecasting features.
- Applying domain-specific business rules to demand projections.
- Integrating multiple datasets into a consolidated analytical output.
- Designing extensible data workflows for future machine learning applications.

**Core Focus:** Data Engineering • Feature Engineering • Time-Series Analysis • Rules-Based Forecasting • Hospitality Revenue Analytics
