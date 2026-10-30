# Supermarket Sales Analysis Dashboard

**File:** `Supermarket_Sales_Dashboard.xlsx`
**Project:** Sapphire IQ | Brilliant Minds Intelligent Solutions – Data Analytics Internship

An interactive Excel dashboard that helps management review overall sales metrics, compare product categories and outlet performance, explore the visibility–sales relationship, and understand statistical patterns in sales.

> **Important:** the workbook ships with **2,000 rows of synthetic sample data** so the dashboard is populated. All figures shown are placeholders until you replace them with the real dataset.

---

## 1. Workbook structure

| Sheet | Purpose |
|---|---|
| **Dashboard** | The management view: filters, KPI cards, 10 charts, statistics table, outlier tables, auto-updating insights. |
| **Analysis** | Calculation tables that feed the dashboard. All formulas; nothing is hard-coded. |
| **Data** | The raw dataset (columns A–L) plus two helper columns (M–N). |
| **About** | Short usage notes inside the workbook. |

### Data columns (row 1 headings)

| Col | Heading | Col | Heading |
|---|---|---|---|
| A | Item Fat Content | G | Outlet Size |
| B | Item Identifier | H | Outlet Type |
| C | Item Type | I | Item Visibility |
| D | Outlet Establishment Year | J | Item Weight |
| E | Outlet Identifier | K | Sales |
| F | Outlet Location Type | L | Rating |

Helper columns (pre-filled formulas, do not overwrite): **M** Z-Score, **N** Outlier Flag (High outlier / Low outlier / Normal).

---

## 2. How to use with your own data

1. Open the **Data** sheet.
2. Delete the sample values in **A2:L2001** (keep the headings and columns M–N).
3. Paste your real records starting at **A2**, as values only, in the same column order.
4. Return to **Dashboard**. Everything recalculates automatically.

Things to check before pasting:
- **Item Fat Content** must read exactly `Low Fat` or `Regular`. Clean variants such as `LF`, `low fat`, `reg` first.
- **Outlet Type** values expected: `Grocery Store`, `Supermarket Type1`, `Supermarket Type2`, `Supermarket Type3`.
- **Outlet Location Type** values expected: `Tier 1`, `Tier 2`, `Tier 3`. **Outlet Size**: `Small`, `Medium`, `High`.
- The 16 Item Types and 10 Outlet Identifiers are listed on the **Analysis** sheet. If your data has different values, edit those labels (and add rows if needed).
- Formulas read **rows 2–3000**. For more than 2,999 records, extend the helper columns M–N and the ranges.

---

## 3. Using the dashboard

Four **yellow dropdowns** at the top filter sections 1–3: Outlet Type, Outlet Location Type, Item Fat Content, Outlet Size. Choose `All` to clear a filter.

Section 4 (statistics) always uses **all records**, regardless of filters.

---

## 4. Objectives and where to find them

### Objective 1 – Overall sales performance
- Total sales revenue, average sales per record, average item visibility (KPI cards; also records count, average rating, top-4 share).

### Objective 2 – Category and outlet-type comparison
- Top 4 categories' share of total sales vs all other categories (doughnut/pie chart and KPI card).
- Highest and lowest sales categories (ranked bar chart; named in Key Insights).
- Total sales by outlet type (column chart).

### Objective 3 – Outlet performance and relationships
- Low Fat vs Regular sales across outlets (clustered column chart).
- Visibility vs sales: scatter plot with trend line, average sales by visibility band, and correlation coefficient with a plain-language trend label.
- Category share of sales within each outlet type (clustered column chart).

### Objective 4 – Statistical analysis
- Average, median, minimum, maximum.
- Variation: range, standard deviation, variance, coefficient of variation, quartiles, IQR, skewness.
- Unusual values: records beyond Q1 − 1.5×IQR or Q3 + 1.5×IQR are flagged as outliers. The dashboard lists the 5 highest and 5 lowest records with Z-scores.
- Average sales by Item Type, Outlet Type and Outlet Location Type (charts).

---

## 5. Method notes

- **Outlier rule:** IQR method (1.5 × IQR fences). Z-scores are shown for reference only.
- **Visibility bands:** 0–0.05, 0.05–0.10, 0.10–0.15, 0.15–0.20, 0.20–0.25, 0.25+. The band limits are blue input cells on the Analysis sheet and can be edited.
- **Correlation:** Pearson correlation between Item Visibility and Sales across all records.
- **Interpretation guide:** below −0.3 strong negative, −0.3 to −0.1 weak negative, ±0.1 little or no linear relationship, 0.1 to 0.3 weak positive, above 0.3 strong positive.
- **Key Insights** at the bottom of the dashboard are formula-driven text, so they update with the data and filters.

---

## 6. Known limitations

- Excel slicers can't be generated programmatically, so dropdown cells are used for interactivity.
- Filters are not applied to the scatter plot or Section 4, which always show all records.
- The sample data is synthetic and not representative of any real business.
