# 🎵 Music Streaming Behavior Analysis — Springfield vs Shelbyville

Exploratory data analysis and hypothesis testing to compare music streaming behavior between users in two cities across different days of the week.

---

## 📌 Overview

Using data from an online music streaming service, this project tests whether user activity differs by city and day of the week — a key insight for content personalization and regional marketing strategies.

**Hypothesis:** User activity on the streaming platform differs depending on the day of the week and the city.

---

## 📊 Dataset

| Feature | Description |
|---|---|
| `user_id` | Unique user identifier |
| `track` | Song title |
| `artist` | Artist name |
| `genre` | Music genre |
| `city` | User's city (Springfield or Shelbyville) |
| `time` | Exact playback time |
| `day` | Day of the week |

- **Raw records:** 65,079
- **After cleaning:** 61,253 (3,826 duplicates removed)

---

## 🔧 Methodology

### Data Preprocessing
- Standardized column names: lowercased, stripped whitespace, applied snake_case (`userid` → `user_id`)
- Filled missing values in `track`, `artist`, and `genre` with `'unknown'`
- Removed 3,826 explicit duplicate rows
- Resolved implicit genre duplicates: `'hip'`, `'hop'`, `'hip-hop'` → standardized to `'hiphop'`

### Hypothesis Testing
- Filtered data for Monday, Wednesday, and Friday
- Grouped by city and day using a reusable `number_tracks(day, city)` function
- Compared track play counts across both cities for each target day

---

## 📈 Results

| Day | Springfield | Shelbyville | Difference |
|---|---|---|---|
| Monday | 15,740 | 5,614 | +10,126 |
| Wednesday | 11,056 | 7,003 | +4,053 |
| Friday | 15,945 | 5,895 | +10,050 |

**Conclusion:** The hypothesis is confirmed — Springfield consistently shows higher playback counts than Shelbyville across all three days. However, this difference may partly reflect population size rather than behavioral patterns alone, as city population data was not available.

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-lightgrey)

- **Python** — Pandas

---

## 📁 Project Structure

```
music-streaming-behavior-analysis/
│
├── S2.ipynb             # Full analysis and hypothesis testing
├── README.md
└── .gitignore
```

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/laaurasaporski/music-streaming-behavior-analysis.git

# Install dependencies
pip install pandas

# Open the notebook
jupyter notebook S2.ipynb
```

---

## 💡 Key Insights

- **Springfield dominates playback volume** across all three days, with roughly 3x more plays than Shelbyville
- **Wednesday shows the smallest gap** between cities — suggesting more balanced mid-week activity
- **Data quality issues were significant:** 3,826 duplicates and 9,108 missing values required treatment before analysis
- **Genre standardization matters:** fragmented labels (`hip`, `hop`, `hip-hop`) can skew genre-based analyses if not consolidated
- **Limitation:** Without population data, raw play counts cannot be normalized per capita — a key caveat for any business decision based on this analysis
