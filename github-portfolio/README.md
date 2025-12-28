# Retail Analytics Dashboard

A real-time business intelligence dashboard built to transform raw POS transaction data into actionable insights. This project demonstrates end-to-end product development from problem identification through deployment.

## Live Demo

[View Demo](https://your-username.github.io/retail-analytics-dashboard)

![Dashboard Screenshot](screenshot.png)

## The Problem

Multi-location retail operations generate thousands of daily transactions, but extracting meaningful insights typically requires:
- Manual spreadsheet analysis taking 4-6 hours weekly
- Delayed decision-making due to data lag
- Inconsistent metrics across locations
- No predictive capability for inventory or customer behavior

## The Solution

I designed and built a dashboard that automatically processes raw CSV exports and delivers:

**Operational Intelligence**
- Real-time KPIs with month-over-month and year-over-year comparisons
- Store-by-store performance benchmarking
- Automated margin alerts for pricing optimization
- Inventory velocity tracking with reorder recommendations

**Customer Analytics**
- RFM-based segmentation (VIP, Regular, Occasional, One-time)
- Churn risk prediction using recency/frequency signals
- Cohort retention analysis
- Cross-category basket analysis for merchandising decisions

**Planning & Forecasting**
- Seasonal index calculations from historical data
- Day-of-week demand patterns for staffing optimization
- 4-week revenue forecasts

## Technical Implementation

**Architecture Decisions**

I chose a serverless, single-page architecture to minimize operational overhead:

- **Frontend**: Vanilla JavaScript with Chart.js for visualizations
- **Data Processing**: Client-side CSV parsing with PapaParse
- **Backend**: Firebase Realtime Database (REST API)
- **Hosting**: Static file hosting (GitHub Pages, Netlify, etc.)

This approach eliminates server maintenance while keeping costs at $0 for typical usage volumes.

**Key Technical Features**

```
├── Client-side data transformation pipeline
│   ├── Multi-file CSV ingestion (transactions + line items)
│   ├── Date parsing with timezone handling
│   ├── Revenue/profit aggregation by multiple dimensions
│   └── Statistical calculations (margins, velocities, indices)
│
├── Interactive data tables
│   ├── Click-to-sort on any column (ascending/descending)
│   ├── Numeric vs. string detection for proper ordering
│   └── Visual sort indicators
│
└── Responsive design system
    ├── CSS custom properties for theming
    ├── Mobile-friendly tab navigation
    └── Accessible color contrast ratios
```

## Product Decisions

**Why no React/Vue/etc?**

For a dashboard with relatively stable data (updated monthly), the complexity of a component framework wasn't justified. Vanilla JS reduced bundle size by 90%+ and eliminated build tooling entirely. The entire application is a single HTML file that works offline.

**Why client-side processing?**

Processing ~50K transactions takes under 2 seconds in-browser. Moving this server-side would add latency, infrastructure costs, and security considerations for sensitive financial data. The data never leaves the user's device until they explicitly save to Firebase.

**Why Firebase over a traditional database?**

The REST API requires zero backend code. Security rules can restrict write access while allowing public reads. The free tier (1GB storage, 100K reads/day) far exceeds this use case's requirements.

## Business Impact

Deployed at a two-location retail operation, this dashboard:

- Reduced weekly reporting time from 5 hours to 15 minutes
- Identified $12K in annual margin leakage through low-margin product alerts
- Improved inventory turnover by surfacing velocity data to buyers
- Enabled data-driven staffing by quantifying day-of-week demand patterns

## Running Locally

```bash
# Clone the repository
git clone https://github.com/your-username/retail-analytics-dashboard.git
cd retail-analytics-dashboard

# Serve locally (any static server works)
python -m http.server 8000
# or
npx serve .

# Open http://localhost:8000
```

The demo loads sample data automatically. No API keys or configuration required.

## Project Structure

```
├── index.html          # Complete dashboard (HTML + CSS + JS)
├── sample-data/
│   └── demo-data.json  # Anonymized sample dataset
└── README.md
```

## About Me

I'm a product leader with 8 years of experience building data products in regulated industries. This project reflects my approach to product development:

1. **Start with the problem** — Observed managers spending hours in spreadsheets
2. **Validate before building** — Paper prototype testing with actual users
3. **Ship incrementally** — MVP with core KPIs, then iterated based on feedback
4. **Measure impact** — Tracked time savings and decisions influenced

Currently exploring opportunities in AI/ML product management, healthcare technology, and B2B SaaS.

[LinkedIn](https://linkedin.com/in/your-profile) • [Email](mailto:your@email.com)

---

*Built with vanilla JavaScript, Chart.js, and Firebase. No frameworks, no build tools, no recurring infrastructure costs.*
