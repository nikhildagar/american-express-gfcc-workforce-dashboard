# American Express GFCC Workforce Planning Dashboard

An interactive Power BI dashboard built to analyze workforce operations, case management, and service performance for the Global Financial Crimes Compliance (GFCC) team at American Express.

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Analytics-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power_Query-Data_Cleaning-success?style=for-the-badge)
![Excel](https://img.shields.io/badge/Excel-Dataset-green?style=for-the-badge)

---

## Project Overview

The Global Financial Crimes Compliance (GFCC) department is responsible for investigating and resolving financial crime and compliance cases across multiple markets. With hundreds of agents and thousands of cases moving through the pipeline at any given time, keeping track of workforce productivity, SLA adherence, and case distribution becomes difficult without a centralized view.

This project takes a raw workforce planning dataset and turns it into a single Power BI report that gives managers a clear, at-a-glance picture of how the department is performing — where the workload is concentrated, how quickly cases are being resolved, and where attention might be needed.

With this dashboard, managers can:

- Monitor workforce productivity in real time
- Track SLA compliance across teams
- Understand how cases are distributed by type, department, and geography
- Evaluate case handling efficiency
- Identify departments or regions carrying a disproportionate workload
- Filter and drill into the data interactively

---

## Objectives

- Analyze the overall case workload handled by the GFCC team
- Measure workforce efficiency at both the individual and team level
- Monitor SLA (Service Level Agreement) compliance
- Track Average Handle Time (AHT) and Average Turnaround Time (TAT)
- Surface and monitor high-priority cases
- Compare performance across departments and countries
- Package all of this into a dashboard that's genuinely usable by non-technical stakeholders

---

## Tech Stack

- **Microsoft Power BI** — dashboard and reporting layer
- **DAX** — measures and calculated KPIs
- **Power Query** — data cleaning and transformation
- **Microsoft Excel** — source dataset
- Data modeling and interactive visualization design

---

## Dataset

| Attribute | Details |
|-----------|---------|
| Total records | 8,022 |
| Total columns | Multiple operational fields |
| Data source | Workforce planning dataset (Excel) |
| Tooling | Excel + Power BI |

---

## Key Metrics

The dashboard is built around six core KPIs that give an immediate read on department health:

| KPI | Result | What it tells you |
|-----|--------|--------------------|
| Total Cases | 8K | Overall case volume processed by the team |
| Average Handle Time | 23.8 hours | How long, on average, agents spend per case |
| SLA Compliance | 94% | Share of cases resolved within agreed timelines |
| Average Turnaround Time (TAT) | — | End-to-end time to close a case |
| Active Agents | 100 | Distinct agents contributing to case resolution |
| High Priority Cases | 2K | Cases flagged as high priority, requiring closer monitoring |

---

## Visualizations

**Monthly Case Trend**
Tracks how case volume moves month over month, making it easy to spot seasonal spikes or emerging backlogs.

**Department-wise Cases**
Compares workload across departments, helping managers spot where teams may be over- or under-resourced.

**Case Type Distribution**
A breakdown of the different categories of cases the team handles, useful for spotting shifts in the nature of the workload.

**Country-wise Cases**
Maps where compliance cases are originating geographically, which is useful for regional resourcing decisions.

**Interactive Filters**
The whole report can be sliced by month, department, priority, and country, so stakeholders can get to the specific view they need without waiting on a custom report.

---

## Business Insights

A few things fall out of the analysis that are worth calling out:

- **SLA performance is strong.** At roughly 94% compliance, the team is meeting its service commitments in the large majority of cases — a solid baseline to maintain or improve on.
- **Workforce utilization looks balanced.** Around 100 active agents are collectively handling 8,000+ cases, without any single glaring imbalance in the aggregate numbers.
- **High-priority cases deserve continued attention.** Roughly a quarter of all cases fall into the high-priority bucket, which is a large enough share that it warrants its own dedicated tracking rather than being folded into general reporting.
- **AHT and TAT are useful diagnostic levers.** Where these numbers creep up, that's usually a sign of process friction worth investigating rather than a workforce capacity issue.
- **Department and country comparisons reveal where to focus.** These views are what make the dashboard actionable — they point to specific teams or regions rather than leaving managers with only an aggregate number.

---

## Data Preparation

The raw dataset needed a fair amount of cleanup before it was ready for reporting. Using Power Query, the following steps were applied:

- Handling missing values
- Correcting data types
- Removing inconsistent or duplicate records
- Standardizing categorical fields (e.g., priority labels, department names)
- Shaping the model so it plays well with the DAX measures built on top of it

---

## DAX Measures

A sample of the core measures powering the dashboard:

```DAX
Total Cases =
COUNTROWS(GFCC_Workforce_Planning_Dataset)
```

```DAX
Active Agents =
DISTINCTCOUNT(GFCC_Workforce_Planning_Dataset[Agent_ID])
```

```DAX
High Priority Cases =
CALCULATE(
    COUNTROWS(GFCC_Workforce_Planning_Dataset),
    GFCC_Workforce_Planning_Dataset[Priority] = "High"
)
```

```DAX
Average Handle Time (Hours) =
DIVIDE(
    AVERAGE(GFCC_Workforce_Planning_Dataset[Handle_Time_Mins]),
    60
)
```

```DAX
SLA Compliance % =
DIVIDE(
    CALCULATE(
        COUNTROWS(GFCC_Workforce_Planning_Dataset),
        GFCC_Workforce_Planning_Dataset[SLA_Met] = "Yes"
    ),
    COUNTROWS(GFCC_Workforce_Planning_Dataset)
)
```

---

## Dashboard Features

- Executive-style KPI cards for at-a-glance reporting
- Interactive slicers for month, department, priority, and country
- Responsive, corporate-themed layout
- Clean visual hierarchy with shadowed cards for KPI emphasis
- Dedicated views for department and country-level analytics
- Trend analysis over time

---

## Dashboard Preview

*(Add your dashboard screenshot here.)*

```markdown
![Dashboard](images/dashboard.png)
```

---

## Project Workflow

```
Excel Dataset
      │
      ▼
Power Query (Data Cleaning)
      │
      ▼
Data Modeling
      │
      ▼
DAX Measures
      │
      ▼
Interactive Dashboard
      │
      ▼
Business Insights
```

---

## Repository Structure

```
American-Express-GFCC-Dashboard
│
├── Dashboard.pbix
├── Dataset.xlsx
├── README.md
├── images/
│   └── dashboard.png
└── Dashboard.pdf
```

---

## Skills Demonstrated

Data cleaning · Data transformation · Data modeling · DAX · KPI development · Business intelligence · Dashboard design · Interactive reporting · Data visualization · Analytical thinking

---

## Future Improvements

- Row-Level Security (RLS) for department- or region-scoped access
- Drill-through pages for case-level detail
- Custom tooltips for richer context on hover
- Dynamic, filter-aware report titles
- Bookmarks for saved views
- Mobile-optimized layout
- Deployment to Power BI Service
- Real-time data refresh

---

## Author

**Yash Dagar**
Data Analyst · Power BI Developer · Business Intelligence Enthusiast

- GitHub: https://github.com/YOUR_USERNAME
- LinkedIn: https://linkedin.com/in/YOUR_LINKEDIN
- Portfolio: https://YOUR_PORTFOLIO

---

If you found this project useful, a star on the repo is always appreciated.
