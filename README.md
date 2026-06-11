# A/B Testing Project

This project presents an end-to-end A/B testing analysis using SQL, Python, and Tableau.

The analysis evaluates the difference between test and control groups across four funnel metrics: impressions, clicks, purchases, and revenue. It includes random split validation, statistical testing, OLAP cube construction, Tableau dashboard development, and segment-level business recommendations.

## Project Links

- [Open Google Colab Notebook](https://colab.research.google.com/drive/12jc3iV7TNbgoZY8TSAg3Philrao66M2u?usp=sharing)
- [View Tableau Dashboard](https://public.tableau.com/app/profile/seoyeon.park.ds/viz/ABTestingPerformanceDashboard/KPIAnalysisABTestingReport)

## Workflow

1. **Data Pipeline Setup SQL**  
   Loaded the required files from cloud storage and created analytical schemas and tables.

2. **A/A Test Sanity Check Python**  
   Checked whether the test/control split was close to 50:50 before running the A/B test.

3. **Initial Statistical Testing Python**  
   Compared test-control differences across impressions, clicks, purchases, and revenue.

4. **OLAP Cube Construction SQL**  
   Created aggregated funnel tables for Tableau, including count, sum, and sum of squares by segment.

5. **Segmented Dashboard Development (Tableau)**  
   Built an interactive [Tableau Dashboard](https://public.tableau.com/app/profile/seoyeon.park.ds/viz/ABTestingPerformanceDashboard/KPIAnalysisABTestingReport) to visualise A/B split, funnel metrics, lift, and 95% significance across age, gender, and date segments.  
   

6. **Segment-Level Insight**  
   Found positive effects in the 0–19 female segment, while the 20–49 female segment showed decreases in purchase and revenue.

## Business Recommendation

The test variant should not be rolled out to all users immediately.  
A limited rollout or further validation could be considered for the 0–19 female segment, while the 20–49 female segment requires further investigation before applying the same variant.

## Tools Used

- SQL
- Python
- Google Colab
- Tableau
- Statistical hypothesis testing
- Funnel analysis
