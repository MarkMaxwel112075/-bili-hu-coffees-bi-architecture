# Bili Hu Coffees BI Architecture
BI system design consolidating Shopify, Excel, Tally ERP and IoT roaster logs into an Azure Synapse warehouse with SARIMA/Prophet demand forecasting and Power BI dashboards.

Engagement Summary

Bili Hu Coffees LLP, a specialty coffee roaster headquartered in Bengaluru, operates across four disconnected systems — Shopify (retail), Excel (wholesale and inventory), Tally ERP (accounting), and IoT-enabled roasting equipment (production logs). Following a structured consultation with Managing Partner Vidyun R. Hebbar, I designed an end-to-end BI architecture to consolidate these sources, automate reporting, and introduce predictive demand planning — addressing the operational reconciliation burden, forecast inaccuracy, and lack of customer behavioural insight identified during discovery.

This repository documents the architecture, data integration design, KPI framework, and predictive modelling approach proposed for the engagement.


Problem Statement

AreaIssue IdentifiedData IntegrationShopify, Excel, Tally ERP and IoT roaster logs operate in isolation — "our systems do not talk to each other." Manual reconciliation obscures real-time inventory visibility, particularly across overlapping wholesale/retail orders.Demand ForecastingForecasting is performed manually in Excel, producing inconsistent results, over/under-roasting, and delayed order fulfilment during peak demand.Customer AnalyticsShopify's native analytics cannot distinguish repeat vs. one-time purchasers or surface high-value customer segments — marketing decisions are made on intuition rather than data.Digital Behaviour TrackingAbsence of GA4 limits visibility into funnel performance, attribution, and the customer's digital journey — constraining subscription growth and geographic expansion plans.


Proposed Architecture

 Shopify   Excel   Tally ERP   IoT Roaster Logs   GA4
    │         │         │              │            │
    └─────────┴─────────┴──────────────┴────────────┘
                          │
                Azure Data Factory (ETL)
                          │
              Azure Synapse Data Warehouse
                  (Star Schema, OLAP)
                          │
            ┌─────────────┴─────────────┐
       Power BI Dashboards        Predictive Models
   (Sales, Inventory, SKU,      (SARIMA / Prophet demand
    Segmentation, IoT QC)        forecasting, churn, RFM)

See /diagrams for the full architecture, ETL pipeline flow, and star-schema ERD.

Core components:


Data Integration: Azure Data Factory pipelines connecting Shopify, Tally ERP, and IoT roaster logs into a single warehouse, removing manual reconciliation.
Warehouse & OLAP: Azure Synapse star-schema warehouse enabling drill-down/roll-up analysis across SKU, time, and customer dimensions.
Predictive Layer: SARIMA and Prophet time-series models for production demand forecasting; k-Means/RFM segmentation for customer retention; churn prediction for the subscription base.
Behavioural Analytics: GA4 integration for funnel analysis, attribution modelling, and CAC tracking.
Reporting Layer: Power BI dashboards replacing manual spreadsheet reporting (target: report generation time reduced from 3–5 hours to under 30 minutes).



KPI Framework

CategoryMetricBaselineTarget (6–12 mo)MechanismForecast AccuracyProduction Forecast (MAPE)Manual, high volatility↓ 10–15%SARIMA / ProphetQuality ControlRoast Profile Variance (IoT)No monitoring↓ 20–25%IoT analyticsStock PerformanceSKU Sell-Through RateManual checks↑ 5–10%OLAP + ClusteringCustomer BehaviourCustomer Lifetime ValueSpreadsheet-based↑ 8–12%Segmentation & retention modelsAcquisition EfficiencyCACManual ad tracking↓ 10–15%GA4 funnel insightsSubscription HealthActive Subscriber RetentionUntracked↑ 5–8%Churn predictionReporting EfficiencyDashboard Generation Time3–5 hrs (manual)< 30 minETL automation

Full KPI tracker with logic and definitions: /kpi-framework


Repository Structure

├── docs/                 → Full written report + architecture notes
├── diagrams/             → BI architecture, ETL flow, star-schema ERD
├── dashboards/           → Power BI mockups (illustrative / synthetic data)
├── kpi-framework/        → KPI tracker spreadsheet
└── models/               → SARIMA/Prophet forecasting demo notebook


Implementation Roadmap


Phase 1 — Foundation: Define KPIs, BI objectives, data sources, and governance.
Phase 2 — Integration: Build ADF ETL pipelines into an Azure Synapse star-schema warehouse.
Phase 3 — Modelling: Develop forecasting, segmentation, churn, and association-rule models; build OLAP cubes.
Phase 4 — Deployment: Roll out Power BI dashboards and GA4, deliver BI literacy training to stakeholders.



Disclosure & Integrity


This case study originates from postgraduate coursework (MG5601, Brunel Business School) based on a real consultation with Bili Hu Coffees LLP's Managing Partner. Company details are disclosed with the founder's knowledge for academic verification.
Financial and operational figures reflect targets and ranges discussed during consultation, not audited client data.
Dashboard visuals in this repository use illustrative or synthetic data and are not connected to Bili Hu's live systems.
Generative AI was used for outline structuring and section-heading refinement only; all analysis and writing are original. Full acknowledgment retained in /docs/full-report.pdf.



Author

Mark Maxwel Louis
Technology Risk Consultant | MSc Accounting & Business Intelligence (Distinction), Brunel University London
SQL · Power BI · DAX · Python (Pandas) · Azure Synapse/ADF

