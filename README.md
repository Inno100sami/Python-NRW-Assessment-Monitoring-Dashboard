# NRW Dashboard — Water Supply Monitoring Tool

> **A production-grade, fully configurable HTML dashboard for Non-Revenue Water (NRW) monitoring.**  
> Works for any number of Water Supply Systems (WSS) and District Metered Areas (DMAs). No server, no installation, no coding required.

🌐 **Live Demo:** [View on GitHub Pages](https://your-username.github.io/nrw-dashboard/)

---

## 📌 Overview

This tool turns NRW operational data into an interactive, browser-based dashboard. It is designed for water utility operators, NRW specialists, and programme managers — especially in low-connectivity environments.

**Any operator can configure it for their own district, systems, and DMAs** using the built-in ⚙️ Configure panel. All settings are saved to the browser automatically.

### Key Features

| Feature | Detail |
|---|---|
| **Multi-WSS support** | Add unlimited Water Supply Systems |
| **Multi-DMA support** | Add unlimited DMAs per WSS, each with its own colour, target, and data |
| **Dynamic filter bar** | Filter all charts by WSS, DMA, and reporting quarter |
| **IWA Water Balance** | Full component tree: input → real losses → apparent losses |
| **7 dashboard sections** | Overview, NRW, Consumption, Leakage, Meters, Interventions, Systems |
| **Offline ready** | Works without internet after first load |
| **Browser storage** | Settings persist across sessions via `localStorage` |

---

## 📊 Dashboard Sections

### 1. Overview
- KPI cards: avg NRW% per DMA, total connections, revenue, IWA losses
- NRW bar chart — all DMAs vs. targets
- IWA Water Balance donut
- Monthly revenue trend and consumption by category
- Summary table of all DMAs with NRW status

### 2. NRW Analysis
- Combined NRW trend line — all filtered DMAs
- Individual mini-chart per DMA with target overlay
- Full IWA Water Balance tree (m³ + %)

### 3. Consumption Analysis
- Stacked monthly consumption by customer category
- Accounts billed and m³/account per month
- Category summary table

### 4. Leakage & Real Losses
- Monthly leakage count and density (leaks/km)
- Average repair response time trend
- Leaking tanks per month
- Real losses breakdown: Mains / Service Connections / Tank Overflows

### 5. Meter Management
- Monthly inspections, age distribution, fault findings
- Actions: Retained vs. Serviced & Returned
- Revenue from meter readings

### 6. NRW Reduction Interventions
- Campaigns and zero-consumption accounts per DMA
- Unbilled metered authorized consumption
- Intervention log with month, description, and cost

### 7. Water Supply Systems
- System specs per WSS (type, year, reservoirs, status)
- NRW targets by DMA
- Network and meter summary
- Revenue by customer category

---

## ⚙️ Configure for Your Utility

Click **⚙️ Configure Dashboard** in the top-right to open the configuration panel.

### Configuration Tabs

| Tab | What You Can Edit |
|---|---|
| 🏢 **Organisation** | District, operator, utility, programme, funder, year, currency |
| 🗺️ **WSS & DMAs** | Add/remove unlimited Water Supply Systems and DMAs. Set name, type, target, network length, connections, aged meter data |
| 💧 **NRW Data** | Monthly NRW % per DMA (auto-populates all charts and KPIs) |
| 📈 **Consumption** | Monthly revenue (12 months), avg by customer category |
| 🔴 **Leakage** | Monthly leakage counts, response times, leaking tanks |
| ⚙️ **Meters** | Totals, age distribution, inspections per month |
| ⚖️ **IWA Balance** | All IWA components in m³ |
| 🛠️ **Interventions** | Summary counts + logged interventions with date and cost |

### Adding a New System

1. Open ⚙️ Configure → **WSS & DMAs** tab
2. Click **＋ Add Water Supply System**
3. Fill in the system name, type, year, and reservoirs
4. Click **＋ Add DMA to this WSS** to add one or more DMAs
5. Fill in DMA name, NRW target, network length, and connections
6. Go to the **NRW Data** tab to enter monthly NRW % for each new DMA
7. Click **✓ Apply & Refresh Dashboard**

---

## 🚀 How to Run

### Option 1 — GitHub Pages (recommended)

1. Fork or clone this repository
2. Go to **Settings → Pages → Source → Branch: `main` → Folder: `/ (root)`**
3. Your dashboard will be live at `https://your-username.github.io/nrw-dashboard/`
4. Update the Live Demo link above with your actual URL

### Option 2 — Open locally (no server needed)

```bash
git clone https://github.com/your-username/nrw-dashboard.git
cd nrw-dashboard
open index.html        # macOS
start index.html       # Windows
xdg-open index.html   # Linux
```

### Option 3 — Local development server

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

> **CDN note:** Chart.js and Google Fonts load from CDN on first open. After that the dashboard works fully offline.

---

## 🏗️ Technical Details

| Feature | Detail |
|---|---|
| **Technology** | Single-file HTML + CSS + JavaScript |
| **Charting** | [Chart.js 4.4.1](https://www.chartjs.org/) via CDN |
| **Fonts** | Space Mono + DM Sans via Google Fonts |
| **Data storage** | Browser `localStorage` — no server, no database |
| **DMA colours** | 12-colour auto-palette, cycles for any number of DMAs |
| **Filter bar** | Filter all charts by WSS, DMA, or quarter |
| **Mobile** | Responsive grid, collapses on narrow screens |
| **Browser support** | Chrome, Firefox, Edge, Safari (ES2020+) |

### Making Fully Offline

To remove CDN dependencies:
1. Download **Chart.js**: `https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js`
2. Download **Google Fonts**: Space Mono + DM Sans, embed via `@font-face`
3. Replace the CDN `<script>` and `<link>` tags with local paths

---

## 📁 Repository Structure

```
├── index.html               # Entry point — redirects to dashboard (GitHub Pages)
├── NRW_Dashboard_v3.html    # Main dashboard — self-contained, fully configurable
├── README.md                # This file
└── data/
    └── *.xlsm               # Original Excel source files (optional reference)
```

---

## 📐 Methodology

All NRW calculations follow the **IWA (International Water Association)** Water Balance standard.

### Key Metrics

| Metric | Definition |
|---|---|
| **NRW %** | `(System Input − Billed Authorised Consumption) / System Input × 100` |
| **Real Losses** | Physical leakage from mains, tanks, and service connections |
| **Apparent Losses** | Metering inaccuracies + unauthorised consumption |
| **Aged Meter** | Meter installed before year 2000 |
| **Leakage Density** | Leaks detected per km of network per month |

### NRW Status Thresholds (colour coding)

| Colour | Condition |
|---|---|
| 🟢 Green | NRW ≤ target |
| 🟡 Amber | NRW > target, ≤ target + 20pp |
| 🔴 Red | NRW > target + 20pp |

---

## 🏢 Sample Data — Institutional Context

The dashboard ships with sample data from Nyabihu District, Rwanda.

| Entity | Role |
|---|---|
| **WASAC** | Water and Sanitation Corporation — asset owner |
| **REDEC** | Private operator — Nyabihu District |
| **VEI B.V.** | Vitens Evides International — technical assistance |
| **Isoko y'Ubuzima** | USAID-funded rural WASH programme (2021–2026) |

---

## 📄 License

This dashboard was developed for operational use within the WASAC / VEI Isoko y'Ubuzima programme. Data is property of WASAC and Nyabihu District. Dashboard code is open for adaptation within WASH sector projects in Rwanda and beyond.

---

*Dashboard version: 3.0 · Sample data: Jan–Jun 2023 · Water Supply Monitoring Tool*
