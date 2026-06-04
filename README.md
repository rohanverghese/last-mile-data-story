# last-mile-data-story
# The 4:00 PM Cliff
### Turning Last-Mile Delivery Data Into a Strategic Story

A data storytelling project: how to take a complex operational problem — first-attempt delivery failure in dense urban zones — and turn it into a narrative that drives a decision, for a **non-technical** operations and executive audience.


---

## The problem

Last-mile delivery is the most expensive leg of the supply chain, and it's where customer experience is won or lost. The specific target here: **first-attempt delivery failure**. When a driver arrives and no one's home, the parcel goes back on the truck — a second trip, a second fuel burn, a second labor cost, and an unhappy customer. The cost hides across thousands of redelivery events instead of showing up as one line item.

Reducing first-attempt failures is one of the few logistics levers that cuts cost **and** lifts satisfaction at the same time.

## The story arc

| Stage | Question | Visual |
|-------|----------|--------|
| **Hook** | When do failures happen? | The 4 PM cliff (line chart) |
| **Rising action** | Where do they cluster, and why? | Choropleth + ranked drivers |
| **Climax** | What's the highest-ROI fix? | Cost waterfall |
| **Resolution** | What's the impact? | Impact dashboard |

### Insight 1 — Failure is a *time* problem

First-attempt failures aren't spread evenly. They climb into a predictable late-afternoon peak — the **4:00 PM cliff** — when recipients aren't home yet and traffic is at its worst.

![Failure rate by hour of day](charts/viz1_cliff.png)

### Climax — The recommendation

Because failures are driven by **absence** in **predictable windows and places**, the highest-ROI move isn't more trucks. It's **shifting high-risk parcels into evening windows** plus **pickup lockers in the worst-offending neighborhoods** — both attack absence directly.

![Cost waterfall: before vs. after intervention](charts/viz2_waterfall.png)

> **Note:** Both charts use **synthetic data** shaped to match real public sources (delivery-failure records are proprietary to carriers). The patterns are realistic; the exact numbers are illustrative.

---

## Data

Real public sources are documented in **[docs/DATA_SOURCES.md](docs/DATA_SOURCES.md)** (NYC TLC, U.S. Census/ACS, USPS, NOAA, OpenStreetMap).

Synthetic sample datasets live in **[`/data`](data)** — see the **[data dictionary](docs/DATA_DICTIONARY.md)**:
- `delivery_failures_by_hour.csv`
- `neighborhood_failure_profile.csv`
- `failure_driver_contributions.csv`
- `cost_waterfall.csv`

## Reproduce

```bash
pip install pandas numpy matplotlib
python scripts/generate_sample_data.py   # regenerates the CSVs (fixed seed)
python scripts/generate_charts.py        # regenerates the chart PNGs
```

## Repo structure

```
.
├── README.md
├── charts/                 # rendered chart PNGs
├── data/                   # synthetic sample CSVs
├── docs/                   # PDF + DOCX deliverables, data docs
└── scripts/                # data + chart generation
```


