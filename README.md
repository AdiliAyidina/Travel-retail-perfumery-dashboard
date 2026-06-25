# Travel-retail-perfumery-dashboard
A full-year, end-to-end analytics project for the travel retail (duty-free) fragrance category: a synthetic but realistically modeled transaction dataset feeding an interactive Google Looker Studio dashboard. Built as a portfolio piece combining domain knowledge of luxury/duty-free retail with data analytics.
# ✈️ Travel Retail Perfumery — Interactive Analytics Dashboard

[![Live Dashboard](https://img.shields.io/badge/Looker%20Studio-Live%20Dashboard-4285F4?logo=googledatastudio&logoColor=white)](https://datastudio.google.com/s/vhHrrPIDVOU)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Generation-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A full-year, end-to-end analytics project for the **travel retail (duty-free) fragrance** category: a synthetic but realistically modeled transaction dataset feeding an interactive **Google Looker Studio** dashboard. Built as a portfolio piece combining domain knowledge of luxury/duty-free retail with data analytics.

### 🔗 [**View the live interactive dashboard →**](https://datastudio.google.com/s/vhHrrPIDVOU)

---

## 📊 Project Overview

This project simulates one year of point-of-sale activity (**2025-06-01 → 2026-05-30**) for a fragrance house operating across three international airports. It demonstrates the complete analytics workflow:

**Data modeling → synthetic data generation (Python) → Google Sheets source → Looker Studio dashboard → insight storytelling.**

The dataset is intentionally engineered with real-world commercial patterns — seasonality, gifting peaks, an event-driven demand spike, and region/airport personality — so the dashboard surfaces genuine business stories rather than random noise.

> ⚠️ **All data is 100% synthetic.** No real customer, sales, or proprietary company data is used. The dataset was generated programmatically for demonstration purposes.

---

## 🖼️ Dashboard Preview

<!-- Replace these with your own screenshots exported from Looker Studio -->
![Dashboard Overview](docs/screenshots/overview.png)
![Dashboard Detail](docs/screenshots/detail.png)

---

## ✨ Dashboard Highlights

The dashboard turns ~16,000 transactions into an explorable commercial story. Key views include:

- **KPI scorecards** — total revenue, transactions, average transaction value (ATV), and units sold.
- **Revenue over time** — monthly trend revealing the summer peak and December gifting spike.
- **Collection mix** — Perfume vs. Body Care vs. Candle contribution to revenue and volume.
- **Top performers** — best-selling fragrances and products (Pareto / top-N).
- **Airport & terminal breakdown** — performance by hub (MAD / CDG / DXB) and terminal.
- **Customer dimensions** — sales split by traveler **region** (APAC / AMER / EAMA / EUEA) and **gender**.
- **Staff performance** — revenue and transactions per sales associate.
- **Interactive filters** — slice the entire report by date range, airport, collection, region, and more.

---

## 📈 Headline Insights

| Insight | Detail |
|---|---|
| 💰 **Total revenue** | **€2.74M** across **15,967** transactions (avg. transaction value ≈ €172) |
| 👑 **Perfume dominates** | Perfume drives **~78%** of revenue, led by premium scents (Oud Velvet, Saffron Ember, Incense Trail) |
| 🎁 **December gifting peak** | Highest-revenue month; Candle & Body Care share rises as travelers buy gifts |
| ☀️ **Summer surge** | July–August form a clear secondary peak driven by holiday travel |
| 🧧 **Chinese New Year event** | Dubai (DXB) sees a **+25%** volume lift and an APAC traveler surge in February |
| 🌍 **Airport personality** | DXB is busiest and APAC-skewed; MAD & CDG lean European (EUEA) |

---

## 🗂️ Dataset

One row = one point-of-sale transaction line. **14 analytical columns** (+ a transaction key).

| Column | Description |
|---|---|
| `transaction_id` | Unique row key |
| `date` / `month` | Sale date and year-month |
| `collection` | Perfume / Body Care / Candle |
| `product` | Item form (e.g. "Eau de Parfum", "Body Lotion") |
| `fragrance` | Scent (20 perfume scents; signature scent per body-care/candle item) |
| `size` | Volume — perfume 100/50/30 ml; body-care & candle fixed per item |
| `volume_units` | Quantity sold |
| `unit_price` / `total_price` | EUR; `total = unit_price × volume_units` |
| `traveler_gender` | F / M |
| `region` | APAC / AMER / EAMA / EUEA |
| `airport` / `terminal` / `staff` | MAD / CDG / DXB · 2 terminals & 3 staff per airport |

**Catalog:** 3 collections — Perfume (20 scents × 3 sizes), Body Care (8 products), Candle (5 products).
📖 Full field-by-field reference: [`docs/data_dictionary.md`](docs/data_dictionary.md).

---

## 🛠️ Tech Stack

- **Google Looker Studio** — interactive dashboard & visualization
- **Google Sheets** — live data source connected to Looker Studio
- **Python** (`pandas`, `numpy`) — synthetic data generation
- **Git / GitHub** — version control & publication

---

## 📁 Repository Structure

```
travel-retail-perfumery-dashboard/
├── data/
│   └── travel_retail_perfumery_2025_2026.csv   # generated dataset (15,967 rows)
├── scripts/
│   └── generate_dataset.py                      # reproducible data generator
├── docs/
│   ├── data_dictionary.md                       # full column & catalog reference
│   └── screenshots/                             # dashboard images for this README
├── README.md
└── LICENSE
```

---

## 🚀 Reproduce the Dataset

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/travel-retail-perfumery-dashboard.git
cd travel-retail-perfumery-dashboard

# 2. Install dependencies
pip install pandas numpy

# 3. Generate the dataset
python scripts/generate_dataset.py
```

The generator uses a **fixed random seed (`42`)**, so every run reproduces the exact same dataset. To feed Looker Studio, upload the resulting CSV to Google Sheets and connect it as a data source.

---

## 🧪 Data Generation Methodology

The dataset is not random — it encodes deliberate commercial logic so analysis yields meaningful findings:

- **Seasonality:** monthly demand multipliers model a summer peak (Jul–Aug) and a December gifting peak; a post-holiday dip follows in January.
- **Event modeling:** a Chinese New Year window (5–22 Feb 2026) boosts DXB volume by 25% and shifts the traveler mix toward APAC.
- **Airport profiles:** each hub has its own base traffic level and region distribution (DXB APAC-heavy; MAD/CDG Europe-heavy).
- **Pricing:** a fixed price book with standard vs. premium perfume tiers; `total_price` is always internally consistent.
- **Behavioral nuance:** weekend uplift, gift-season quantity increases, and collection-specific gender skews.

---

## 👤 About

**Aella (Adili Ayidina)** — Data Analyst with a background in luxury fragrance and travel retail (Le Labo / Estée Lauder, Global Blue), and an MSc in Business Analytics. Trilingual: Mandarin · Spanish · English.

This project sits at the intersection of two of my domains — **duty-free fragrance retail** and **data analytics** — using realistic category dynamics I know first-hand to build a portfolio-ready, end-to-end BI workflow.

- 🔗 LinkedIn: `<your-linkedin-url>`
- 📧 Contact: `<your-email>`

---

## 📜 License

Released under the [MIT License](LICENSE). The synthetic dataset is free to use for learning and demonstration.

---

### ✅ Personalize before publishing
- [ ] Add your GitHub username to the clone URL
- [ ] Export 1–3 dashboard screenshots to `docs/screenshots/` (the README references `overview.png` and `detail.png`)
- [ ] Confirm the **Dashboard Highlights** match your actual report pages/charts (I couldn't read the live charts — only the dataset)
- [ ] Fill in your LinkedIn and contact details
- [ ] Add a `LICENSE` file if you keep the MIT badge (GitHub can generate one in two clicks)
