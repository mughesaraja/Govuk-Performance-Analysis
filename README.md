# GOV.UK Passport Renewal — Performance Analysis

A end-to-end performance analysis project modelled on the tools,
methods and KPI frameworks used by the Government Digital Service (GDS).

**View the live Looker Studio dashboard →https://datastudio.google.com/reporting/0dd8aaf9-af21-4383-93bb-1673b3607868**

---

## Project overview

This project simulates the work of a Performance Analyst embedded in a
GOV.UK product team. Using a realistic synthetic GA4 event dataset of
2,000 user sessions across a passport renewal journey, it covers:

- Defining what success looks like through a KPI performance framework
- Funnel analysis to identify where users drop off
- Segmentation by device and traffic source to surface actionable insights
- Data quality validation before any results are published
- A live Looker Studio dashboard replicating a GDS show-and-tell output

---

## Tools and technologies

| Tool | Purpose |
|---|---|
| Python (pandas, numpy) | Data simulation and analysis |
| SQL (SQLite) | BigQuery-style querying and funnel analysis |
| Google Sheets | Data storage and Looker Studio connector |
| Looker Studio | Live performance dashboard |
| Google Colab | Analytical environment |
| GitHub | Version control and portfolio hosting |

---

## The service journey

The analysis covers a seven-stage transactional service journey:

1. `/apply-renew-passport` — landing page
2. `/apply-renew-passport/eligibility` — eligibility checker
3. `/apply-renew-passport/photo` — photo requirements
4. `/apply-renew-passport/personal-details` — user details form
5. `/apply-renew-passport/check-answers` — review screen
6. `/apply-renew-passport/payment` — payment page
7. `/apply-renew-passport/confirmation` — completion

---

## KPI framework

Before any analysis, success metrics were defined upfront — consistent
with GDS performance measurement standards.

| KPI | Result |
|---|---|
| Task completion rate | 7.4% |
| Biggest drop-off point | Payment page (55.5%) |
| Average journey time (completers) | ~9 minutes |
| Highest completing traffic source | Paid search (10.4%) |
| Best completing device | Desktop |

---

## Key findings

**1. Payment page is the critical drop-off point**
55.5% of users who reached the payment page did not proceed to
confirmation. This warrants qualitative investigation — likely causes
include fee visibility, trust signals, and card payment friction.
Recommendation: A/B test an improved payment page with clearer fee
summary and security reassurance copy.

**2. Mobile users complete at a lower rate than desktop**
Despite accounting for 52% of sessions, mobile users completed the
journey at a lower rate than desktop users. GOV.UK forms are
content-heavy and not optimised for small screens at this stage.
Recommendation: Review the personal details and check-answers pages
on mobile viewport sizes with a user researcher.

**3. Paid search brings the highest-intent users**
Users arriving via paid search completed at 10.4% — the highest of
any traffic source. This suggests the ad targeting is reaching users
who are ready to complete, justifying the spend.
Recommendation: Share this finding with the campaign team to inform
budget allocation toward paid search.

---

## Data quality validation

Before publishing any results, seven automated checks were run:

- No missing values across all columns
- No duplicate events
- All page paths match the expected journey
- No journey order violations (page skipping)
- All timestamps within the expected date range
- All device and traffic source values valid
- No sessions with suspiciously high event counts (bot detection)

**Result: all checks passed.**

---

## Project structure
govuk-performance-analysis/

│

├── govuk_performance_analysis.ipynb   # Full analysis notebook

├── data/

│   ├── ga4_events.csv                 # Simulated raw GA4 event data

│   ├── funnel_summary.csv             # Funnel drop-off by page

│   ├── completion_by_device.csv       # Completion rate by device

│   ├── completion_by_source.csv       # Completion rate by source

│   └── weekly_sessions.csv            # Session volume over time

└── README.md
---

## About this project
Built as a portfolio project to demonstrate performance analysis skillsaligned with the GDS Performance Analyst role and the Government Digital and Data Capability Framework. All data is synthetic and generated using Python — no real user data was used at any point.
