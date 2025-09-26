
# Employee Returns and Performance Dashboard

[![Power BI Dashboard Screenshot](link-to-your-first-screenshot.png)](link-to-your-github-raw-screenshot)  
[![Power BI Dashboard Page 2 Screenshot](link-to-your-second-screenshot.png)](link-to-your-github-raw-screenshot)

## Project Overview
This repository contains a Power BI dashboard analyzing sales, returns, and employee performance for US-based orders from 2014-2016. The dashboard highlights key metrics like return rates, total sales (~194K), profit by region, and employee-specific returns. Data was cleaned in Power Query, modeled with relationships, and enhanced with DAX measures for YoY comparisons and KPIs.

The goal is to identify trends in returns (e.g., high returns by employee Anna or in Office Supplies category) and provide actionable insights for reducing returns and improving performance.

## Data Sources
The dataset includes:
- **People.xlsx**: Employee list with regions (e.g., Anna - West).
- **Returns.xlsx**: Returned orders (595 entries, with Order IDs and "Yes" flags).
- **orders2014.csv**: Sales data for 2014 (~1,000 rows).
- **orders2015.csv**: Sales data for 2015 (~2,000 rows).
- **orders2016.csv**: Sales data for 2016 (~2,000 rows).
- **Employement_Returns&Performance.pdf**: Exported dashboard visuals (2 pages) for quick reference.

Data covers categories (Furniture, Office Supplies, Technology), regions (Central, East, South, West), and metrics like Sales, Profit, Discount, and Returns.

## Dashboard Features
- **LiveDashboard.pbix**: The core Power BI file.
  - **Cleaning in Power Query**: Merged/appended CSV files, fixed text quantities (e.g., "two" -> 2), handled date formats, removed duplicates/truncations.
  - **Data Modeling**: Star schema with fact (Orders/Returns) and dimension tables (People, Date hierarchy). Relationships on Order ID and Region/Person.
  - **DAX Measures** (examples):
    - `Total Returns = DISTINCTCOUNT(Returns[Order ID])` → 297.
    - `Return Rate = DIVIDE([Total Returns], [Order Count])` → 0.33.
    - `Return Rate YoY = CALCULATE([Return Rate], SAMEPERIODLASTYEAR('Date'[Date]))` → 4.07.
    - Employee-specific: `Return Count (Employee) = CALCULATE([Total Returns], FILTER(Orders, Orders[Region] = RELATED(People[Region])))`.
    - Others: Avg Refund Value, Total Sales, Profit by Region.
  - **Visuals**: KPIs (cards/gauges), pies (regions/employees), bars (top cities/categories), lines (monthly/YoY returns), tables (top returns/customers), slicers (Region, Ship Mode, Year).
  - **Themes**: Blue color scheme with emojis for engagement.

To use: Download `LiveDashboard.pbix` and open in Power BI Desktop (free from Microsoft). Interact with slicers for filtering.

## How to Use
1. Clone the repo: `git clone https://github.com/yourusername/Employee-Returns-Performance-Dashboard.git`.
2. Open `LiveDashboard.pbix` in Power BI Desktop.
3. Refresh data if needed (data sources are local files in the repo).
4. Explore visuals: Filter by region (e.g., West) to see Anna's high returns (28 total).
5. For online viewing: Publish to Power BI Service and share the link.

## Insights from Analysis
- Total Returns: 297 (~0.33 rate), up 4.07 YoY.
- Top Employee Returns: Anna (28), Magee (11).
- Regions: South has highest profit; West/East lead in returns.
- Categories: Office Supplies has most returns (32, ~$3,572).
- Trends: Peaks in Sep/Dec; Standard Class shipping dominates sales.

## Requirements
- Power BI Desktop (version 2.0+ recommended).
- No external dependencies; all data is self-contained.

## Contributing
Fork the repo, make changes (e.g., new DAX), and submit a pull request.

## License
MIT License - feel free to use and modify.

## Contact
Created by [Your Name]. Questions? Open an issue or email [your.email@example.com].
