# 📊 Meta Ads Analytics Dashboard

> Power BI dashboard for Facebook & Instagram ad performance — built from 400K raw events across 4 CSV tables.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=flat)
![Meta Ads](https://img.shields.io/badge/Meta%20Ads-0866FF?style=flat&logo=meta&logoColor=white)
![Rows](https://img.shields.io/badge/Rows-400K-purple?style=flat)

---

## 📂 Raw Data — 4 CSV Tables

| Table | Rows | Raw Columns |
|-------|------|-------------|
| ad_events | 400,000 | event_id, ad_id, user_id, timestamp |
| ads | 200 | ad_id, campaign_id, ad_platform, ad_type, target_gender, target_age_group, target_interests |
| campaigns | 50 | campaign_id, name, start_date, end_date, duration_days, total_budget |
| users | 9,841 | user_id, user_gender, user_age, age_group, country, location, interests |

---

## 🔧 Power Query Transformations

### ad_events (4 cols → 9 cols)
- Fixed `timestamp` data type: text → DateTime
- **Added** `day_of_week` — extracted from timestamp
- **Added** `time_of_day` — Morning / Afternoon / Evening / Night
- **Added** `event_type` — derived event category
- **Added** `Event Date` — date part for Calendar table join
- **Added** `Event Hour` — hour integer for hourly trend chart

### campaigns
- Fixed `start_date` and `end_date`: text → Date

---

## 📐 Data Model (Star Schema)

```
campaigns (1) ──→ (N) ads (1) ──→ (N) ad_events (N) ←── (1) users
                                         │
                                    Calendar Table (1:N on Event Date)
```

---

## 📈 Dashboard KPIs

| Metric | Value |
|--------|-------|
| Impressions | 216K |
| Clicks | 25.4K |
| Shares | 1.3K |
| Comments | 2.6K |
| Purchases | 1.3K |
| Engagements | 29.3K |
| CTR | 11.76% |
| Engagement Rate | 13.56% |
| Conversion Rate | 5.2% |
| Purchase Rate | 0.61% |
| Total Budget | $2.5M |
| Avg Budget/Campaign | $50.7K |

---

## 🏆 Ad Type Performance

| Ad Type | Impressions | Clicks | CTR | Conv. Rate |
|---------|------------|--------|-----|------------|
| Video | 15.1K | 1.8K | 11.78% | 5.6% |
| Stories | 23.8K | 2.7K | 11.35% | 5.6% |
| Image | 16.8K | 1.9K | 11.23% | 5.2% |
| Carousel | 15.9K | 1.8K | 11.08% | 5.2% |

---

## 🛠 Tools Used

- **Power BI Desktop** — report canvas & visuals
- **Power Query (M)** — data type fixes, column additions
- **DAX** — custom measures (CTR, CVR, Purchase Rate, Engagement Rate)
- **Calendar Table** — time intelligence (YTD, MTD, weekly trends)
- **Dynamic Measure Slicer** — switch between KPIs on-the-fly

---

## 📸 Dashboard Preview

![Dashboard Preview](dashboard.png)

---

⭐ If you found this useful, give it a star!
