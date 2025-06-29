# 📊 ShiftStats

**ShiftStats** is a quick-turn analytics project that demonstrates how to transform raw shift-tracking data into clear, actionable reporting for a fictional on-demand labor platform.

---

## ✅ Project Goal

This project answers two main business questions for a pretend operations team and leadership:

1. **Status Update** — How are shifts being offered, accepted, and completed across the company’s network?
2. **Data Integrity Check** — Are there any data quality issues (like duplicate records or unexpected sparsity) in the raw shift tracking data?

---

## 🗂️ What’s Included

- **Python Jupyter Notebook:**  
  Used for exploratory data analysis (EDA), data cleaning, aggregations, and generating a weekly metrics summary.
- **PostgreSQL Database:**  
  Cleaned and aggregated shift data is written to a local Postgres instance.
- **Metabase (via Docker Compose):**  
  Connects to the Postgres database to build interactive dashboards and simple visualizations for stakeholders.
- **Basic ETL Logic:**  
  Raw CSV → Cleaned pandas DataFrame → Weekly metrics → Stored in Postgres → Visualized in Metabase.

---

## ⚙️ How It Works

1. **Raw Data Ingest:**  
   The notebook loads synthetic shift data containing shift UUIDs, store info, roles, dates, times, wage potential, completion status, and geo-dispatch info.

2. **Data Integrity Checks:**

   - Duplicate UUID checks (`df.duplicated()`)
   - Nulls, outliers, and suspicious values flagged for review

3. **Aggregation:**

   - Weekly roll-ups for `shifts_sent`, `shifts_accepted`, `shifts_completed`, `no_shows`
   - Calculation of week-over-week % change for each metric

4. **Database Write:**  
   Using SQLAlchemy, the cleaned data and weekly aggregates are written to a Postgres table (`metrics_daily`).

5. **Visualization:**  
   Metabase (running in Docker) connects to the local Postgres database. Dashboards visualize key trends for operations and flag potential data issues.

---

## 🧩 How to Run

**Clone the repo**

```bash
git clone https://github.com/yourusername/shiftstats.git
cd shiftstats
```

**Create and activate a virtual environment
**

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Run the Jupyter Notebook

```
bash
jupyter notebook
```

Follow the notebook steps to:

- Load and clean the data

- Write aggregated results to Postgres

**Start Metabase
**

```bash
docker compose up -d
```

Open http://localhost:3000 and connect Metabase to your local Postgres.

**Explore Dashboards
**
Use Metabase to build and share charts like:

- Total shifts sent vs. accepted vs. completed

- Week-over-week % changes

- Data issues flagged

📌 Notes

The project uses only open source tools: Python, pandas, PostgreSQL, Docker, and Metabase.

This is a demonstration for interview purposes — the data is synthetic.

Designed to showcase quick EDA, lightweight pipeline, and practical dashboarding for ops stakeholders.

## 👤 [Find Chris Adan on LinkedIn](https://www.linkedin.com/in/chrisadan/)

### [Read on Medium](https://upandtothewrite.medium.com/)
