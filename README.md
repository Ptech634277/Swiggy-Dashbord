# Swiggy Orders Dashboard

An interactive, Power BI-style analytics dashboard for food-delivery order data, built as **one self-contained HTML file**. No backend, no installation, no build step. Open it in a browser and the report is ready.

The report design stays fixed. The data underneath can be swapped at any time through Excel, CSV or Google Sheets.

```
Data Source  →  Validation  →  Processing  →  Dynamic Report  →  Export
```

> Add a screenshot here: `![Dashboard](docs/screenshot.png)`

---

## The problem this project solves

Order data usually lives in spreadsheets with thousands of rows. Nobody can read that and answer simple business questions quickly. The typical pain points are:

| Problem | How the dashboard solves it |
|---|---|
| Raw rows are unreadable | KPI cards and charts summarise 1,200 orders at a glance |
| Every new question needs a new pivot table | Click any bar, slice or period and the whole report filters instantly |
| Reports are rebuilt by hand every time the data changes | Upload a new file or connect a Google Sheet and the same report regenerates |
| Bad or incomplete files break the report silently | Files are validated and previewed before anything is shown |
| Testing a report risks overwriting real data | Sample data is a separate dataset and never touches your own |
| Sharing results means screenshots | One-click Excel report, CSV, or Print / PDF export |
| Heavy BI tools need licences and setup | A single HTML file, free, works offline after the libraries load |

---

## What the data actually shows

These are the real numbers from the included dataset (`Swiggy_Orders.xlsx`, 1,200 orders, Jan 2017 to Nov 2023). The point of the dashboard is to surface facts like these in seconds.

| Metric | Value |
|---|---|
| Total orders | 1,200 |
| Total order value | ₹6,61,655 |
| Swiggy revenue | ₹65,564 |
| Average order value | ₹551 |
| Take rate (revenue ÷ order value) | 9.9% |
| **On-time delivery** | **50.6% (607 on time, 593 delayed)** |

**The headline finding:** nearly half of all orders were delivered late. Volume is healthy and spread evenly (no city has more than 136 orders, none fewer than 102), so the real issue in this dataset is delivery reliability, not demand.

Where the delays concentrate:

| Dimension | Best on-time rate | Worst on-time rate |
|---|---|---|
| City | Mumbai and Jaipur, 58% | Hyderabad and Pune, 41% |
| Restaurant | Royal Dine and Spice House, 55% | Food Express, 42% |
| Payment type | Credit Card, 56% | Wallet, 44% |
| Year | 2021, 56% | 2022, 46% |

Volume trend: yearly orders grew from 158 (2017) to 185 (2023), and order value peaked in 2022 at about ₹1.05 lakh.

**How much to trust these numbers:** each city has only about 100 to 136 orders, so a gap of a few points between two middle-ranked cities is likely noise. The extremes (41% vs 58%) are large enough to be worth investigating, but treat them as leads, not proof of cause. The dashboard shows what happened. It does not explain why.

---

## Features

- **KPI cards:** orders, order value, Swiggy revenue, average order value, revenue per order, on-time %, each compared with the overall total.
- **Charts:** trend by year, quarter or month with an on-time line; delivery status and payment doughnuts; bars by city, food and restaurant.
- **Cross-filtering:** click any chart element to filter everything; each chart keeps its own full list and highlights your selection.
- **Filters:** year, city, delivery status, food, restaurant, payment type.
- **Measure switch:** view every chart by Orders, Order value or Swiggy revenue.
- **5 themes:** Light, Dark, Blue, Green, Corporate, applied to cards, charts, tables and backgrounds.
- **Full-screen report view** with a one-click exit.
- **Data sidebar:** upload Excel or CSV, connect Google Sheets, load sample data, download a template, switch between datasets.
- **Upload popup:** shows file name, rows, columns, validation result and a data preview before you confirm.
- **Data safety:** uploads are added as separate datasets by default; replacing data always asks for confirmation.
- **Export:** Excel report (summary, orders and breakdown sheets), CSV, and Print / PDF, for the filtered view or all data.

---

## Questions and answers about the problems it solves

**Q1. What business question does this report answer?**
How much are we selling, how much do we earn from it, and how reliably do we deliver? It breaks that down by time, city, food, restaurant and payment type.

**Q2. What is the most important insight in the current data?**
Only 50.6% of orders arrive on time. Demand is evenly spread and growing slowly, so delivery reliability is the biggest opportunity. Hyderabad, Pune, Food Express and Wallet payments have the weakest on-time rates.

**Q3. Does it tell me why deliveries are late?**
No. The dataset has no delivery time, distance, rider or weather columns, so the dashboard can only show where delays happen. Finding the cause needs more data.

**Q4. Can I trust the city and restaurant rankings?**
Use them as indicators. With roughly 100 to 190 orders per group, small differences are not statistically reliable. Large gaps are more meaningful.

**Q5. Why not just use Excel pivot tables?**
Pivots need rebuilding for every question. Here one click on a chart re-filters every KPI and chart at once, and the same report layout reloads when the data changes.

**Q6. What happens when my data changes?**
Upload the new file, or refresh a connected Google Sheet. The report regenerates with the same design. You do not rebuild anything.

**Q7. What if my file has the wrong columns or bad rows?**
Validation runs first. Missing required columns block the upload with a clear message. Rows with an invalid date or amount are skipped and counted, and you see that before confirming.

**Q8. Will loading sample data overwrite my real data?**
No. Sample data is generated as its own dataset and tagged "Demo data". Switch back to your data any time and it is exactly as you left it, including your filters.

**Q9. Can I accidentally lose my uploaded data?**
Not through normal use. New uploads are added as separate datasets. Replacing is a deliberate option and asks "Are you sure you want to replace the current data?" first.

**Q10. Is my data sent to a server?**
No. Everything is processed in your browser. There is no backend. Only the Google Sheets link option contacts Google, to read your sheet.

**Q11. Can I share the report with a client?**
Yes. Export an Excel report or CSV, print to PDF, or host the HTML file (for example on GitHub Pages). The main screen is kept clean: all data tools sit in the collapsible sidebar.

**Q12. Can I use it for a different restaurant or company?**
Yes, as long as the data has the same nine columns (see below). The logo and title are in the HTML and easy to change.

---

## Data format

Required columns (names are matched case-insensitively):

| Column | Example |
|---|---|
| Order ID | ORD1001 |
| Food Name | Biryani |
| Order Date | 2024-01-15 |
| Restaurant Name | Royal Dine |
| Order Price | 420 |
| Payment Type | UPI |
| City | Mumbai |
| Revenue to Swiggy | 46.2 |
| Delivery Status | Ontime or Delay |

Use **Download Template** in the sidebar to get a ready-made file. Dates like `15/03/2024` are read as day/month/year.

---

## How to use

1. Open the HTML file in a browser (or host it with GitHub Pages).
2. Click the **☰** button to open the sidebar.
3. Choose **Upload Data**, pick Excel, CSV or Google Sheets, review the validation and preview, then click **Generate Report**.
4. Click chart elements and filters to explore. Use **Full screen** for presenting.
5. Use **Download** in the header to export Excel, CSV or PDF.

**Publish on GitHub Pages:** rename the file to `index.html`, push it to your repository, then go to *Settings → Pages* and select your branch.

---

## Honest limitations

- **Data is not saved between sessions.** Reloading the page returns to the original dataset.
- **Google Sheets:** the sheet must be shared as "Anyone with the link can view". Browsers or hosting environments that block requests to Google will fail. In that case use **Paste copied cells** or upload the sheet as `.xlsx` or `.csv`. Pasted data cannot be auto-refreshed.
- **Needs internet for libraries.** Chart.js and SheetJS load from a CDN. Download them locally for fully offline use.
- **Descriptive analytics only.** No forecasting, no statistical testing, no causes.
- **Fixed schema.** The nine columns above are required.
- **The sample dataset is synthetic.** It exists for demonstration only and should never be used for decisions.

---

## Tech stack

- HTML, CSS and vanilla JavaScript
- [Chart.js 4.4](https://www.chartjs.org/) for charts
- [SheetJS](https://sheetjs.com/) for reading and writing Excel and CSV

---
*********************************************** https://ptech634277.github.io/Swiggy-Dashbord/ *****************************************************
## Author

Dashboard developed and designed by **Prashant Sharma**.
