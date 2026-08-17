# A/B Testing Project

This project evaluates the impact of an A/B test across the user behavior funnel and analyzes how experiment effects vary by age, gender, and date segments.
It includes the development of Tableau dashboards for KPI monitoring and segmented A/B analysis, helping identify target segments for rollout and areas requiring further validation.

## Project Links

- [Open Google Colab Notebook](https://colab.research.google.com/drive/1_DS48PIWWIUy5n91Y5utejMmfK6plaQj?usp=sharing)
- [View Tableau Dashboard](https://public.tableau.com/app/profile/seoyeon.park.ds/viz/ABTestingPerformanceDashboard/KPIAnalysisABTestingReport)
- View Slides


## Workflow

1. **Data Preparation & Schema Setup (SQL)**  
   Loaded user, assignment, and event data from Amazon S3, performed EDA, and built a relational raw-data schema.

2. **A/A Assignment Sanity Check (Python)**  
   Validated the hash-based test/control assignment and confirmed no statistically significant imbalance before the A/B test.

3. **Overall A/B Test (Python)**  
   Aggregated user behavior at the user-day level and tested differences in Impression, Click, Purchase, and Revenue using independent two-sample t-tests.

4. **Segment-Level Aggregation (SQL)**  
   Built an OLAP-style table by date, age, and gender with `n`, `sum`, and `sum2` to support repeated segment-level A/B testing.

5. **KPI Monitoring & A/B Testing Dashboard (Tableau)**
   Built dashboards to monitor CTR, CVR, AOV, and ARPU and to compare funnel-stage Test–Control effects and statistical significance across segments.

7. **Segment Insight & Drill-down**  
   Identified different effects by age and gender, and detected a negative anomaly on Jan 16 that was especially concentrated among users aged 20–49.

---

## Business Recommendation

The test variant should not be rolled out uniformly to all users.

- **Validate the Jan 16 anomaly first** by checking possible system, operational, or experiment-related causes.
- For **0–19 users**, consider a limited rollout and monitor whether the positive Click, Purchase, and Revenue effects are reproduced.
- For **20–49 users**, maintain the current version and re-test the experimental elements due to declines in Purchase and Revenue.
- For **50+ users**, maintain the current version since no significant effect was observed.
- Conduct **follow-up tests by gender** to identify why male upper-funnel gains did not translate into purchases and which experimental elements contributed to the decline in female purchases.

## Tools Used

- SQL
- Python
- Google Colab
- Tableau
- Claude
- Statistical hypothesis testing
- Segment / Funnel analysis
