# Enhancing SME Performance through BI: A System Design for Bili Hu Coffees LLP

A Business Intelligence system design built for a real client, Bili Hu Coffees LLP, a specialty
coffee roaster based in Bengaluru, India, completed as part of my MSc Business Intelligence
module at Brunel University London.

## What this is

I interviewed the company's Managing Director, Vidyun Hebbar, to understand how the
business actually operates day to day, then designed (not implemented) a BI system to
address the specific problems he described, rather than working from a generic template.
This is consulting analysis and system design, the recommendations have not been built or
deployed by the company.

## The company's actual problem

Bili Hu runs Shopify for retail orders, Excel for wholesale and inventory, Tally ERP for
accounting, and IoT-enabled roasting equipment that logs batch data nobody was analysing.
None of these systems talk to each other. In Hebbar's own words, the team has to manually
reconcile numbers because "our systems do not talk to each other," and forecasting is done
in Excel in a way he described as "typically reactive."

## What I designed

- An **Azure Synapse data warehouse** as the single integrated environment, consolidating
  Shopify, Excel, Tally ERP, IoT logs, and GA4 into one source of truth
- An **automated ETL pipeline** (Azure Data Factory) to remove the manual reconciliation
  that was costing the team hours per week
- **OLAP cubes** for SKU-level, multi-dimensional analysis (the specific report Hebbar asked
  for: comparing SKU performance over time and catching early product trends)
- **Predictive models** (SARIMA, Prophet, regression) for demand forecasting, directly
  targeting the over-roasting and waste caused by reactive, spreadsheet-based planning
- **Customer segmentation** (RFM scoring, K-Means clustering) and **churn prediction** to
  support the subscription retention goals Hebbar raised
- **Power BI dashboards** and **GA4 integration** for ongoing decision support and digital
  funnel analysis, which the business had no visibility into previously

## Projected impact (KPI targets, 6–12 months post-implementation)

| Area | Target |
|---|---|
| Production forecast accuracy (MAPE) | Down 10–15% |
| Roast quality variance | Down 20–25% |
| SKU sell-through | Up 5–10% |
| Customer lifetime value | Up 8–12% |
| BI report generation time | Down from 3–5 hours to under 30 minutes |
| Subscriber retention | Up 5–8% |

## Implementation roadmap proposed

1. Define KPIs, BI objectives, data sources, and governance
2. Build ETL pipelines and the Azure Synapse star-schema warehouse
3. Build forecasting, segmentation, and churn models; build OLAP cubes
4. Deploy Power BI and GA4; deliver BI literacy training to staff

## A note on scope and use of AI

This was graded coursework (MG5601, Brunel University London). Generative AI (ChatGPT)
was used for idea generation and outline structuring only, consistent with the university's
academic guidance on AI use; all analysis and writing are my own. This is a system design
exercise based on a real client interview, not an implemented or deployed solution.

## About

Built by [Mark Maxwel Louis](https://www.linkedin.com/in/markmaxwellouis), MSc Accounting
& Business Intelligence (Distinction), Brunel University London, for a real consulting
engagement with Bili Hu Coffees LLP ([bilihucoffee.com](https://bilihucoffee.com)).
