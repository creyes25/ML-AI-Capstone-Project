### Project Title
Predicting Task Duration to Identify Automation Opportunities

**Author**
Author: Carolina Reyes

---
#### Executive summary

Administrative teams often lose hours each week to repetitive workflow tasks such as approvals, ticket handling, purchasing requests, and reimbursements. These tasks vary widely in duration, which creates bottlenecks, delays, and unnecessary rework.

This project applies machine learning and time series forecasting to analyze an incident management workflow. The goal is to predict step-level task duration, and forecast daily workflow volume to support staffing and automation decisions.

Several models were evaluated, ranging from simple baselines to tree-based regressors and time series models. Results show that task duration is highly predictable using event-level data. A Linear Regression model achieved an MAE of ~44 minutes with an R² of 0.77, while tree-based models further reduced error. Time series forecasting demonstrated that daily ticket volume is stable and predictable.

Together, these findings show that administrative workflows follow consistent patterns and are strong candidates for targeted automation and process optimization.

---
#### Rationale

Manual workflows waste time, create delays, increase burnout, reduce accuracy and drain administrative resources. Without understanding how long tasks take and where delays occur, organizations struggle to prioritize automation and staffing improvements. 

By predicting task duration and forecasting workload, organizations can:

- Identify bottlenecks and high-impact automation opportunities

- Balance workload across staff

- Reduce rework and escalation cycles

- Improve efficiency without increasing headcount

Understanding task duration and workload trends is a foundational step toward data-driven automation.

---
#### Research Question

Which workflow characteristics best predict how long a task will take to complete, and how can forecasting daily workload support staffing and automation decisions?

#### Data Sources

Dataset sourced from Kaggle: Process Mining Event Log - Incident Management 

Event-level workflow data includes:

- Case IDs, 
- Timestamps
- Event types
- Priority, 
- Issue type, 
- Resolver
- Report Channel

This dataset mimics the structure of real administrative workflows and supposrts analysis of:

- Step-level task duration
- Case complexity
- Escalation patterns
- Workflow bottlenecks
- Daily workload trends

---
#### Methodology

1. Data Preprocessing

- Converted timestamps to datetime
- Sorted events by Case ID and timestamp
- Filled missing Resolver values with “Unassigned”
- Removed duplicates and validated event ordering

2. Feature Engineering

- Step Duration (target variable): computed time between each event and the next event within a case.
- Case Cycle Time: Total minutes per case.
- Case Complexity: Number of events per case.

3. Exploratory Data Analysis

Visualizations Included:
- Event frequency
- Daily ticket workload
- Priority distribution
- Resolver workload
- Number of steps per case
- Variant frequency

4. Modeling
   
Task Duration Prediction (Regression)
Four models were evaluated:
- Baseline (Dummy Regressor):
  - MAE: ~94.8 minutes
  - R² ≈ 0
  
- Linear Regression:
  - MAE: ~44.2 minutes
  - R²: 0.77
  
- Decision Tree Regressor:
  - MAE: ~39.3 minutes
  - R²: ~0.78
- Random Forest Regressor:
  - MAE: ~30.5 minutes
  - R²: ~0.87

Time Series Forecasting (Daily Ticket Volume)

- Aggregated events by day
- Used differencing to make the series stationary
- Built a baseline forecast (previous-day value)
- Applied an ARMA model to forecast daily ticket volume

Results:
- Baseline Forecast MAE: ~60.6 events
- ARMA Forecast MAE: ~54.1 events
  
The ARMA model outperformed the baseline, showing that daily workload follows predictable temporal patterns.

---
#### Results

Key Findings:

- Task duration is highly predictable using event-level features

- Linear Regression explains ~77%.

- Tree-based models further reduce error but increase complexity

- Case complexity strongly impacts duration — longer workflows take longer

- Resolver workload is unevenly distributed

- Daily ticket volume is stable and forecastable

Conclusion: 

Administrative workflows exhibit strong structural patterns. Even simple models can reliably predict task duration and workload volume. These findings support the use of automation for intake, routing, and triage, as well as proactive staffing based on forecasted demand. This project establishes a data-driven foundation for improving efficiency without sacrificing quality or increasing staff burnout.

---
#### Next steps

- Tune tree-based models to balance performance and interpretability
- Extend time series forecasting to weekly or monthly horizons
- Add features such as L2/L3 escalation flags and resolver workload metrics
- Simulate automation scenarios to estimate time savings and cycle time reduction
- Develop real-time task prioritization tools for administrators

---
#### Outline of project

- [View Jupiter Notebook](https://github.com/creyes25/ML-AI-Capstone-Project/blob/main/Capstone_Jupyter.ipynb)

---
##### Contact and Further Information

For questions:
Carolina Reyes
carolina.reyes2022@gmail.com