# Tableau Sales & Customer Dashboards

Two interactive Tableau dashboards designed to help sales managers, executives, marketing teams, and management explore sales performance and customer behavior.

This project compares a selected year with the previous year, highlights sales and profit trends, and helps users understand customer purchasing patterns.

> **Project status:** Requirements defined. This README describes the intended solution based on `sales-dashboard-requirements.pdf`. A dataset, Tableau workbook, screenshots, and published dashboard URL were not supplied with the requirements.

## Project Objectives

- Analyze year-over-year sales, profit, and quantity performance.
- Identify seasonal patterns and high- and low-performing periods.
- Compare product subcategory sales and profitability.
- Understand customer activity, order frequency, and customer value.
- Enable users to explore historical performance through interactive filters.

## Platform

**Tableau** is the required visualization platform. The data source, preparation tools, and publishing environment will be determined during implementation.

## Sales Dashboard

| Component | Requirements |
| --- | --- |
| KPI overview | Show total sales, total profit, and total quantity for the selected year and the previous year. |
| Monthly trends | Display monthly values for each KPI for both years, clearly identifying the months with the highest and lowest sales. |
| Product subcategory comparison | Compare sales by product subcategory across both years and compare sales with profit. |
| Weekly sales and profit | Display weekly sales and profit for the selected year alongside their respective weekly averages; distinguish weeks above and below the average. |

## Customer Dashboard

| Component | Requirements |
| --- | --- |
| KPI overview | Show total customers, sales per customer, and total orders for the selected year and the previous year. |
| Monthly trends | Display monthly values for each customer KPI for both years and make the months with the highest and lowest sales easy to recognize. |
| Customer order distribution | Show the number of customers grouped by how many orders they placed, supporting analysis of loyalty and engagement. |
| Top 10 customers by profit | Rank the 10 most profitable customers and show their rank, number of orders, current sales, current profit, and last order date. |

## Interactivity and Filters

Both dashboards must support:

- **Year selection:** Explore any year available in the dataset and compare it with the immediately preceding year.
- **Dashboard navigation:** Move easily between the Sales and Customer dashboards.
- **Chart interactions:** Click chart elements to filter the displayed data.
- **Product filters:** Category and subcategory.
- **Location filters:** Region, state, and city.

In this project, **current year** means the year selected by the user, rather than necessarily the calendar year today.

## Data Requirements

The requirements do not specify a dataset or source schema. The following is a proposed minimum field mapping; actual column names may differ.

| Field | Purpose |
| --- | --- |
| Order ID | Count distinct orders and calculate customer order frequency. |
| Order Date | Support year selection, monthly and weekly trends, and last order dates. |
| Customer ID | Count distinct customers and aggregate customer performance. |
| Customer Name | Label the top customer ranking. |
| Sales | Calculate revenue and sales per customer. |
| Profit | Analyze profitability and rank customers. |
| Quantity | Calculate total units sold. |
| Category / Subcategory | Support product comparisons and filters. |
| Region / State / City | Support geographic filters. |

Use data at a grain that preserves product detail, such as one row per order line. An order may span multiple rows, so order counts must use distinct Order IDs. Check that relationships or joins do not duplicate sales, profit, or quantity.

## Metric Definitions

The following definitions are proposed for implementation and should be validated against the final dataset and business rules.

| Metric | Definition |
| --- | --- |
| Total sales | Sum of Sales within the applicable period and filters. |
| Total profit | Sum of Profit within the applicable period and filters. |
| Total quantity | Sum of Quantity within the applicable period and filters. |
| Total customers | Distinct Customer IDs with orders within the applicable period and filters. |
| Total orders | Distinct Order IDs within the applicable period and filters. |
| Sales per customer | Total sales divided by total customers within the same period and filters. |
| Orders per customer | Distinct Order IDs for each customer within the applicable period and filters. |
| Customer profit | Sum of Profit for each customer within the applicable period and filters. |
| Last order date | Latest Order Date for each customer; confirm whether this should use the selected period or full customer history. |
| Average weekly sales / profit | Mean of the corresponding weekly totals over the defined comparison weeks. |

Before building calculations, confirm the week start day, treatment of partial weeks and weeks without transactions, currency, returns and cancellations, and whether incomplete years should compare equivalent year-to-date periods. For zero denominators or missing prior-year data, show an explicit unavailable value rather than a misleading result.

## Implementation Workflow

1. **Prepare the data:** Identify the dataset, confirm its grain, map required fields, validate dates and numeric types, and resolve duplicates and missing identifiers.
2. **Build the data model:** Connect the source in Tableau and validate relationships or joins against source totals.
3. **Create calculations:** Add a selected-year parameter, current- and previous-year measures, customer and order counts, sales per customer, and weekly averages.
4. **Build Sales worksheets:** Create KPI views, monthly comparisons, product subcategory comparisons, and weekly sales and profit trends.
5. **Build Customer worksheets:** Create KPI views, monthly comparisons, order-frequency distribution, and the top 10 customer table.
6. **Assemble the dashboards:** Add navigation, year selection, product and location filters, and chart filter actions.
7. **Validate and document:** Check totals and interaction behavior, capture screenshots, and document workbook access and refresh steps.

## Using the Completed Dashboards

Once the Tableau workbook or published view is available:

1. Open the workbook in a compatible Tableau authoring application, or open its published view.
2. If using a local workbook, resolve any required data connections.
3. Select a year to display its performance alongside the previous year.
4. Apply category, subcategory, region, state, or city filters.
5. Click interactive chart elements to explore a subset of the data.
6. Use the navigation controls to switch between Sales and Customers.
7. Clear chart selections and filters to return to the broader view.

Workbook-specific setup instructions and a live dashboard link should be added after implementation.

## Validation Checklist

- [ ] Sales, profit, and quantity totals reconcile with the source data.
- [ ] Customer and order counts use distinct identifiers.
- [ ] Year selection updates all relevant worksheets and prior-year comparisons.
- [ ] Monthly trends display the correct year pair and highlight sales extrema correctly.
- [ ] Subcategory comparisons show both years and include profit context.
- [ ] Weekly averages follow the agreed week and period definitions.
- [ ] Customer distribution counts customers once within each order-frequency group.
- [ ] The top 10 ranking uses profit and a documented tie-breaking rule.
- [ ] The customer table includes rank, orders, sales, profit, and last order date.
- [ ] Product, location, and chart filters affect the intended views consistently.
- [ ] Dashboard navigation works in both directions.
- [ ] Missing data, empty selections, and zero-customer periods display clearly.

## Planned Deliverables

- Tableau workbook containing the Sales and Customer dashboards.
- Documented data source and metric definitions.
- Dashboard screenshots for project documentation.
- Published dashboard link, if publication is part of the final delivery.

## Requirements Reference

The dashboard features above reflect the supplied requirements. Data-field mappings, metric conventions, and the implementation workflow are proposed guidance until confirmed during development.
