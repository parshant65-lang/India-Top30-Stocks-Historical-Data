# India Top 30 Publicly Traded Equities (1-Minute Historical Market Data Archive)

An institutional-grade, open-source archive of cleaned, standardized, and validated **1-minute intraday historical candlestick data** for **India's Top 30 Blue-Chip Companies** (Sensex 30 Benchmark Universe) with daily automated cloud ingestion.

---

## 🏛️ Directory Architecture & Strict Date-Wise Hierarchy

Every stock is strictly organized into daily CSVs partitioned by Year/Month/Date:

```text
India-Top30-Stocks-Historical-Data/
├── RELIANCE/
│   └── 1m/
│       ├── README.md
│       └── 2026/
│           └── 10/
│               ├── RELIANCE_1m_2026-10-01.csv
│               ├── RELIANCE_1m_2026-10-05.csv
│               └── RELIANCE_1m_2026-10-09.csv
├── TCS/
│   └── 1m/
│       ├── README.md
│       └── 2026/10/...
└── ... [All 30 Companies]
```

---

## 📊 Dataset Overview
- **Constituents:** 30 Benchmark Companies (Sensex 30)
- **Timeframe:** 1 Minute (`1m`)
- **Total Archived Daily Files:** `270` sessions
- **Total 1-Minute Candles:** `97,474` candles
- **Last Ingested:** `2026-10-13 18:20:07 UTC`
- **Trading Sessions:** Monday – Friday, 09:15 to 15:30 IST (03:45 to 10:00 UTC)

---

## 📑 Data Schema (Uniform Across All Files)

| Column Name | Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `timestamp` | `int64` | Candle open time in Unix milliseconds (UTC) | `1791517500000` |
| `datetime_utc` | `string` | Standard ISO human-readable UTC timestamp | `2026-10-09 03:45:00` |
| `open` | `float64` | Opening price in INR | `1178.60` |
| `high` | `float64` | Highest price reached during the 1-minute window | `1178.90` |
| `low` | `float64` | Lowest price reached during the 1-minute window | `1174.50` |
| `close` | `float64` | Closing price of the 1-minute candle | `1176.30` |
| `volume` | `float64` | Cumulative volume traded in the 1-minute candle | `42645` |

---

## ⚡ 1-Line Pandas Stream Loader (No Clone Required)

Stream any stock's 1-minute data directly from GitHub's raw CDN into Pandas in 1 second:

```python
import pandas as pd

# Load Reliance Industries 1-minute data for October 09, 2026
url = "https://raw.githubusercontent.com/parshant65-lang/India-Top30-Stocks-Historical-Data/main/RELIANCE/1m/2026/10/RELIANCE_1m_2026-10-09.csv"
df = pd.read_csv(url)
print(df.head())
```

---

## 🔄 Daily Automated Cloud Ingestion
A GitHub Actions workflow runs every weekday post-market (**Monday to Friday at 15:30 IST / 10:00 UTC**) to query Yahoo Finance, slice newly closed 1-minute sessions into daily CSVs, de-duplicate timestamps, and commit updates automatically.
