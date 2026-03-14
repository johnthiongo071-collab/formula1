
# 🏎️ Formula 1 Data Analytics

Exploratory data analysis of Formula 1 race data (2009–2018) using Python, SQLite, and interactive HTML visualisations. The project queries a structured F1 database across 13 tables — from lap times and pit stops to driver standings and constructor results — to uncover patterns in race performance, reliability, and team dominance.

---

## 📁 Repository Structure

```
formula1-analytics/
├── Formula1.sqlite          # Source database (13 tables)
├── f1.ipynb                 # Jupyter notebook — EDA & base visualisations
├── f1_visualizations.html   # Interactive dashboard — Top Drivers, Constructors, Shortest Races
├── f1_full_dashboard.html   # Extended dashboard — 5 in-depth analyses with SQL code
└── README.md
```

---

## 📊 Visualisations

### `f1_visualizations.html` — Core Charts
Three tabbed charts matching the notebook's magma palette style:

| Tab | Chart | Query Tables |
|-----|-------|-------------|
| 🏆 Top Drivers | Horizontal bar — top 10 drivers by race wins | `drivers`, `results` |
| 🔧 Top Constructors | Horizontal bar — top 10 constructors by race wins | `constructors`, `results` |
| ⏱ Shortest Races | Line chart — fastest winning race time per season | `races`, `results` |

### `f1_full_dashboard.html` — Extended Analysis
Five deeper analyses, each with an expandable SQL + Python code block and a written insight:

| Tab | Chart Type | Key Finding |
|-----|-----------|-------------|
| Pole → Win Rate | Bar chart | Pole position wins ~40% of races; P1+P2 account for ~59% of all wins |
| Driver Nationalities | Horizontal bar | British & German drivers account for ~65% of all wins in this period |
| Constructor Seasons | Multi-line | Clear three-era story: Brawn → Red Bull → Mercedes dominance |
| DNF Reasons | Doughnut chart | Engine failures lead (~18%), closely followed by collisions (~16%) |
| Pit Stop Speed | Horizontal bar | Red Bull & Mercedes are ~4 seconds faster per stop than the slowest teams |

---

## 🗄️ Database Schema

The `Formula1.sqlite` database contains 13 tables:

```
circuits            — circuit locations and metadata
races               — race calendar by season
drivers             — driver biography and nationality
constructors        — constructor/team information
results             — race results per driver per race
driver_standings    — cumulative championship points
constructor_standings
constructor_results
laptimes            — per-lap timing data
pitstops            — pit stop timings and durations
qualifying          — qualifying session results
seasons             — season-level metadata
status              — result/retirement status codes
```

---

## 🛠️ Setup & Usage

### Prerequisites

```bash
pip install pandas matplotlib seaborn jupyter
```

### Run the Notebook

```bash
git clone https://github.com/your-username/formula1-analytics.git
cd formula1-analytics
jupyter notebook f1.ipynb
```

The notebook connects to `Formula1.sqlite` in the same directory:

```python
import pandas as pd
import sqlite3
import seaborn as sns
import matplotlib.pyplot as plt

conn = sqlite3.connect('Formula1.sqlite')
curr = conn.cursor()
```

### View the Dashboards

Open either HTML file directly in a browser — no server required:

```bash
open f1_full_dashboard.html        # macOS
start f1_full_dashboard.html       # Windows
xdg-open f1_full_dashboard.html    # Linux
```

---

## 💡 Key Insights

- **Qualifying is decisive** — starting from pole converts to a win 40% of the time. By P5, that drops below 5%.
- **Mercedes' hybrid era dominance** — from 2014 onward, Mercedes won 85–95% of races per season, an unprecedented run in the modern era.
- **Reliability matters** — engine failures are the single biggest cause of retirement, accounting for nearly 1 in 5 DNFs.
- **Pit crew performance is a weapon** — the gap between the fastest (Red Bull) and slowest pit crews is ~4 seconds per stop, which regularly determines track position.
- **F1 talent is geographically concentrated** — British and German drivers won ~65% of all races in this period, driven almost entirely by Hamilton and Vettel.

---

## 📌 Data Coverage

| Attribute | Detail |
|-----------|--------|
| Seasons | 2009 – 2018 |
| Total races | 997 |
| Drivers | All race entrants across both decades |
| Lap times | Available from `laptimes` table |
| Pit stops | Full duration data in `pitstops` table |

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Data wrangling and analysis |
| SQLite3 | Database querying |
| Pandas | DataFrames and pivoting |
| Seaborn / Matplotlib | Notebook visualisations |
| Chart.js | Interactive HTML dashboard charts |
| HTML / CSS / JS | Dashboard UI |

---

## 📄 License

This project is for educational and analytical purposes. F1 data sourced from the [Ergast Developer API](http://ergast.com/mrd/) database export.
