 Crop Diversification Index — Jharkhand

A district-wise agricultural analysis of Jharkhand (2002–2010), examining production trends, crop concentration risk, seasonal dependency, and production anomalies across all 24 districts.

 Project Overview

This project measures how reliant each district in Jharkhand is on a single crop, using the Herfindahl-Hirschman Index (HHI) as a diversification risk score. It combines Python for data cleaning and analysis with Power BI for an interactive, client-facing dashboard.

Key finding: 19 of Jharkhand's 24 districts are classified as "Concentrated" (high mono-cropping risk), with rice as the dominant crop in 23 of 24 districts. Only Khunti qualifies as genuinely diversified.

Data Source

- Dataset: District-wise crop production data for India (Kaggle: "Crop Production in India")
- Filtered to: Jharkhand only — 24 districts, 12 crop types
- Time period: 2002–2010
- Columns: State_Name, District_Name, Crop_Year, Season, Crop, Area (hectares), Production (tonnes)

 Methodology

 Data Cleaning (Python)
- Filtered raw India-wide dataset to Jharkhand districts only
- Stripped whitespace and standardized district/crop/season names
- Verified no missing values, duplicates, or zero-area records


 Diversification Risk Score (HHI)
For each district, the Herfindahl-Hirschman Index is calculated as:

```
HHI = Σ (crop_area_share)²
```

Where `crop_area_share` is each crop's proportion of the district's total cultivated area. Districts are classified as:
- HHI < 0.15 → Diversified
- HHI 0.15–0.25 → Moderate
- HHI > 0.25 → Concentrated (high risk)

Anomaly Detection
Year-over-year production deviations are flagged using Z-scores and percentage deviation from each district's historical average, highlighting years with unusually sharp production drops (e.g., Chatra district's 81% production drop in 2010).
 Files in This Project

 File Description 

 `jharkhand_clean.csv`  Master cleaned dataset (1,266 rows, 24 districts) 
 `district_summary.csv`  District-wise production, yield, and rankings 
`crop_diversification_index_jharkhand.pbix`  Power BI dashboard file 

 Dashboard Structure (Power BI)

1. Summary
Landing page with production trends, district rankings, the Risk Diversification chart (19 Concentrated / 4 Moderate / 1 Diversified), and a Jharkhand map shaded by risk band.

2. Production Details
Year-by-year, district-by-district production and yield table with a supporting map — used for drilling into specific figures.

3. Anomaly
Flags districts and years with statistically unusual production drops, using Z-score and percentage deviation. Includes narrative callouts on the most significant anomalies (e.g., Chatra 2010).

4. Season Comparison
Compares production across Kharif, Rabi, Winter, Autumn, and Whole Year categories per district. Reveals that Winter season production dominates in most districts.

Tools Used

- Python (pandas): Data cleaning, HHI calculation, aggregation, anomaly detection
- Power BI: Interactive dashboard — filters, maps, charts, drill-through, reset bookmarks

Key Takeaways

1. Jharkhand's agriculture is overwhelmingly rice-dependent across nearly all districts — a state-wide structural risk, not a localized issue.
2. Most districts also depend heavily on the Winter season for production, adding a second layer of seasonal risk.
3. 2010 stands out as an anomalous year with sharp production drops across multiple districts simultaneously, warranting further investigation (e.g., against rainfall/weather data).
4. Crop diversification support should be prioritized in the districts flagged "Concentrated," starting with the most extreme cases (East Singhbhum, West Singhbhum, Saraikela Kharsawan — all above 93% rice dependency).

 Limitations

- Dataset covers only 2002–2010 and 12 crop types — the fuller government APY dataset (40+ crops, up to 2024-25) would give a more complete and current picture.
- HHI scores may overstate concentration if farmers grow additional minor crops not captured in this dataset.
- No rainfall or weather data is included, limiting root-cause analysis of the 2010 production anomaly.
