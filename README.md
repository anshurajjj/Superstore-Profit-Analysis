# 📊 Superstore Sales & Profitability Dashboard | Power BI

An interactive **Power BI Sales & Profitability Analysis Dashboard** designed to analyze sales performance, profitability, regional contributions, product performance, and monthly sales trends. This project demonstrates business intelligence reporting, DAX calculations, data modeling, and interactive report design.

The dashboard uses a dark executive-style theme with KPI cards, interactive regional filtering, conditional formatting, and drillthrough navigation to support data-driven business decisions.

---

## 📸 Dashboard Preview

### Regional Sales & Profitability Analysis

![Regional Sales and Profitability Dashboard](images/regional-details.png)

The Regional Details page provides a focused view of regional performance, including sub-category sales, monthly sales trends, top-performing states, and profit by region.

> **Note:** Save the screenshot in your repository's `images` folder as `regional-details.png`. If your filename differs, update the image path above.

---

## 🎯 Project Objectives

- Monitor overall sales, profit, profit margin, and order volume.
- Compare sales performance across regions and product categories.
- Identify high-performing states, products, and sub-categories.
- Analyze monthly sales trends and changes over time.
- Evaluate profitability alongside revenue to support better decisions.
- Enable interactive exploration through slicers and drillthrough.
- Present business performance through a professional, executive-style report.

---

## 📌 Key Performance Indicators (KPIs)

The following values are visible in the supplied Regional Details screenshot.

| KPI | Displayed Value |
|---|---:|
| Total Sales | 2.33M |
| Total Profit | 292.30K |
| Profit Margin | 12.56% |
| Total Orders | 5,111 |

**Important:** These figures reflect the displayed report context. Slicers, filters, and date selections can change KPI values and rankings. Confirm the filter state before interpreting them as full-dataset totals.

---

## 📊 Dashboard Features

### 1. Executive Overview

The main report page provides a high-level view of business performance through:

- KPI cards for Total Sales, Total Profit, Profit Margin, and Total Orders.
- Sales analysis by region and category.
- Top products by sales.
- Monthly and annual sales trends.
- Profitability analysis by sub-category.
- Sales contribution analysis.
- Sales distribution by shipping mode.
- Average discount monitoring.
- Year-over-year sales analysis.

### 2. Regional Details

The Regional Details page enables deeper regional analysis through:

- Interactive region selector with a **Select All** option.
- KPI cards for sales, profit, profit margin, and orders.
- Horizontal bar chart for Total Sales by Sub-Category.
- Monthly sales trend using Year-Month.
- Top 10 States by Sales.
- Profit by Region with conditional formatting.
- Navigation back to the main report page.
- Drillthrough for focused regional investigation.

### 3. Interactive Reporting

- Region-based filtering.
- Cross-filtering between supported visuals.
- Drillthrough navigation.
- Conditional formatting for profitability comparisons.
- Chronologically sorted month and Year-Month fields.
- Consistent dark navy report background with white visual containers.

---

## 🗂️ Data Model

The report uses the following tables:

| Table | Purpose |
|---|---|
| `Orders` | Sales, profit, order dates, products, categories, and related order-level fields |
| `People` | Regional lookup information |
| `Returns` | Return-related information |
| `Dim_Date` | Calendar table for time-based analysis |

### Date Table and Relationships

- The `Dim_Date` table spans **3 January 2023 to 30 December 2026** in the current model.
- An active one-to-many relationship connects `Dim_Date[Date]` to `Orders[Order Date]`.
- The relationship uses single-direction filtering.
- Month names are sorted by Month Number.
- Year-Month labels are sorted using a numeric Year-Month sort column.

A dedicated date table supports consistent time intelligence and chronological analysis in Power BI.

---

## 🧮 DAX Measures

The following are representative measures used in the report.

### Total Sales

```dax
Total Sales =
SUM('Orders'[Sales])
```

### Total Profit

```dax
Total Profit =
SUM('Orders'[Profit])
```

### Profit Margin %

```dax
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

### Sales Contribution %

```dax
Sales Contribution % =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        REMOVEFILTERS(Orders[Region])
    ),
    0
)
```

This measure calculates sales as a share of the total across regions while retaining other applicable filters.

### Sales Previous Year

```dax
Sales Previous Year =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(Dim_Date[Date])
)
```

### Sales YoY Growth %

```dax
Sales YoY Growth % =
DIVIDE(
    [Total Sales] - [Sales Previous Year],
    [Sales Previous Year],
    0
)
```

Format percentage measures as percentages in Power BI. Validate time-intelligence results against the selected reporting period and date-table configuration.

---

## 💡 Business Analysis Approach

### 1. Sales and Profitability

Evaluate total sales and total profit together to understand revenue generation and financial contribution. Profit margin adds context by showing how much profit is generated relative to sales.

### 2. Regional Performance

Compare regional sales and profit to identify differences in commercial performance. A region with high sales may not necessarily have the highest profit margin, so both measures should be reviewed.

### 3. Product and Sub-Category Analysis

Use sales rankings and sub-category comparisons to identify products that contribute strongly to revenue. Review profitability alongside sales before prioritizing products or categories.

### 4. Monthly Sales Trends

Analyze sales by Year-Month to identify peaks, declines, and changes over time. Use consistent date filters when comparing periods.

### 5. State-Level Analysis

Use the Top 10 States by Sales visual to identify leading states by revenue. Additional analysis of profit and margin can help determine whether high sales also translate into strong profitability.

### 6. Discount and Return Analysis

Investigate whether discount levels and returned orders are associated with weaker profitability. Further analysis is required before attributing a change in profit to a particular factor.

---

## 🛠️ Tools and Techniques

- **Power BI Desktop** — dashboard development and interactive reporting
- **DAX** — KPI calculations, profit margin, sales contribution, and year-over-year analysis
- **Power Query** — data preparation and transformation, where applied
- **Data Modeling** — relationships, date dimensions, and sorting
- **Data Visualization** — KPI cards, bar charts, trend charts, and donut charts
- **Conditional Formatting** — visual comparison of profitability
- **Slicers and Drillthrough** — interactive report exploration

---

## 🔍 Data Interpretation and Limitations

- KPI values and rankings can change according to slicers, page filters, visual filters, and date selections.
- Screenshot values represent the displayed report context, not necessarily the entire dataset.
- Highest sales does not automatically mean highest profit or highest profit margin.
- Trends and correlations do not independently establish the cause of a business outcome.
- The currency is not specified in this README. Add a currency symbol only after confirming the source data's currency.
- The PBIX file and source data should only be shared publicly if you have permission to distribute them.

---

## 📁 Repository Structure

```text
superstore-sales-profitability/
│
├── README.md
├── images/
│   └── regional-details.png
└── Superstore-Sales-Profitability.pbix
```

The `.pbix` file is optional in the public repository. Include it only if you are permitted to share the report and its underlying data.

---

## 🚀 How to Explore the Report

1. Download or clone the repository.
2. Open `Superstore-Sales-Profitability.pbix` in Power BI Desktop, if included.
3. Start with the main report page to review the overall KPIs and sales trends.
4. Use the region selector and other available filters to explore the data.
5. Open the Regional Details page to compare sub-categories, states, monthly sales, and regional profit.
6. Compare sales, profit, and margin together before drawing conclusions.

---

## 🧠 Skills Demonstrated

- Power BI dashboard development
- DAX measures and KPI reporting
- Data modeling and date-table configuration
- Time-intelligence calculations
- Interactive slicers and drillthrough
- Conditional formatting and data visualization
- Regional and product performance analysis
- Profitability analysis
- Business insight communication
- Analytical validation and interpretation

---

## 👨‍💻 Author

**Anshu Raj**

Data Analyst | Power BI | SQL | Python | Excel | Business Intelligence

---

⭐ If you find this project useful, consider starring the repository and sharing feedback.
