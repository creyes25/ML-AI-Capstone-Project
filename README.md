### Project Title
Predicting Task Duration to Identify Automation Opportunities

**Author**
Author: Carolina Reyes

---
#### Executive summary

Administrative teams often lose hours each week to repetitive workflow tasks such as approvals, ticket handling, purchasing requests, and reimbursements. These tasks vary widely in duration, which creates bottlenecks, delays, and unnecessary rework.

This project uses machine learning to predict step-level task duration within an incident management workflow. By identifying which events take the longest and which factors most strongly influence duration, managers can determine where automation will have the greatest impact.

A simple Linear Regression model achieved an MAE of ~44 minutes and an R² of 0.77, demonstrating that workflow duration is highly predictable. This suggests that automated triage, routing, and process optimization can meaningfully reduce delays and improve efficiency.

---
#### Rationale

Manual workflows waste time, create delays, increase burnout, reduce accuracy and drain administrative resources. If task duration can be predicted, organizations can identify bottlenecks, target automation opportunities, balance workload, and reduce staff pressure. Understanding task duration is a key foundation for data-driven automation decisions.

--
#### Research Question

Which workflow characteristics best predict how long a task will take to complete, and where does automation offer the most time-saving potential?

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

- Step durations
- Case complexity
- Escalation patterns
- Workflow bottlenecks

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
- Daily workload
- Priority distribution
- Resolver workload
- Steps per case
- Variant frequency

4. Modeling

Two models were built for comparison:

- Baseline Model (DummyRegressor): 
  - MAE: ~94.84 minutes
  - R² ≈ 0

- Simple Linear Regression Model:
  - MAE: 44.21 minutes
  - R²: 0.77
  - Reduced prediction error substantially compared to baseline and explained 77% of variance

---
#### Results

Key Findings:

- Workflow duration is highly predictable using event-level features
- Linear Regression reduced prediction error significantly compared to the baseline model.
- Case complexity impacts duration: workflows with more steps tend to take longer.
- Resolver workload is imbalanced, with a small number of resolvers handling a large share of events.
- Daily workflow volume is stable, supporting reliable planning and forecasting.

Conclusion: 

A simple ML model (Linear Regression) can predict workflow durations. These results support the idea that organizations can improve efficiency through automation of intake and triage, reduction of rework, identification of high-impact automation steps, and better workload balancing. This project provides a foundation for data-driven workflow automation in administrative operations.

---
#### Next steps

- Train additional models (Decision Tree Regression, etc.) and compare performance to Linear Regression
- Implement time series analysis/forecasting to predict daily ticket volume
- Add features such as L2/L3 escalation flags and resolver workload metrics
- Simulate automation scenarios to estimate time savings and cycle time reduction
- Help administrators prioritize tasks

---
#### Outline of project

- [View Jupiter Notebook](https://github.com/creyes25/ML-AI-Capstone-Project/blob/main/Capstone_Jupyter.ipynb)

---
##### Contact and Further Information

For questions:
Carolina Reyes
carolina.reyes2022@gmail.com