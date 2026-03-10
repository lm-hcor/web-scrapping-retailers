# 🛒 Global Grocery Index

A web scraping project that compares grocery prices across **Walmart** (USA), **Mercadona** (Spain), and **DIA** (Spain) — standardised to EUR and metric units for fair comparison.

> 📊 **Live Dashboard → [lm-hcor.shinyapps.io/web-scrapping-retailers](https://lm-hcor.shinyapps.io/web-scrapping-retailers/)**

---

## 📁 Repository Structure

```
web-scrapping-retailers/
├── app.R                        # Shiny dashboard (run this to launch)
├── data/
│   └── cpi_master_data_final.csv  # Pre-scraped data (ready to use)
├── scraping/
│   └── finalproj.qmd            # Full scraping pipeline (optional re-run)
└── README.md
```

---

## ▶️ How to Reproduce

### Option A — Just launch the dashboard (recommended)
The pre-scraped data is already in `/data`. No scraping needed.

**1. Clone the repo**
```bash
git clone https://github.com/lm-hcor/web-scrapping-retailers.git
```

**2. Install dependencies**
```r
install.packages(c(
  "httr", "jsonlite", "openssl", "purrr", "tibble",
  "readr", "robotstxt", "dplyr", "rvest", "stringr",
  "shiny", "shinydashboard", "tidyverse", "DT", "fmsb"
))
```

**3. Launch the dashboard**
```r
shiny::runApp()
```

---

### Option B — Full pipeline (re-scrape + launch)
Run this if you want to regenerate fresh data from the three supermarkets.

**1–2.** Same as above.

**3. Run the scraping pipeline**

Open `scraping/finalproj.qmd` in RStudio and run all chunks.  
This will regenerate `data/cpi_master_data_final.csv`.

> ⚠️ **Note:** The Walmart scraper requires a valid `private_key.pem` and consumer ID from the [Walmart Affiliate API](https://developer.walmart.com/). Mercadona and DIA scrape publicly accessible pages.

**4. Launch the dashboard**
```r
shiny::runApp()
```

---

## 🔍 What the Dashboard Shows

| Feature | Description |
|---|---|
| Price Comparison | Mean unit price per supermarket (filterable by category) |
| Radar Chart | Full pricing footprint across all 5 product categories |
| KPI Boxes | Avg price, cheapest store, price volatility, item count |
| Raw Data Explorer | Full scraped dataset with search and pagination |
| Methodology Tab | Data sources, conversion logic, and ethical scraping notes |

---

## 🌍 Data Sources & Methodology

| Supermarket | Method | Currency | Units |
|---|---|---|---|
| Walmart | REST API (authenticated) | USD → EUR | Imperial → Metric |
| Mercadona | JSON API | EUR | Metric |
| DIA | HTML scraping (rvest) | EUR | Metric |

- Exchange rates fetched live from the [Frankfurter API](https://www.frankfurter.app/)
- Ethical scraping practices applied: `robots.txt` checked, `Sys.sleep()` delays, custom user-agent headers

---

## 👥 Authors
Danielle Rivas (https://github.com/babygal21), Luis Miguel Herrera Corrales (https://github.com/lm-hcor), David Valero Regalón.


IE University — Web Scraping Project, 2026
