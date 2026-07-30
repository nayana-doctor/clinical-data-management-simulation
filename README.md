# Clinical Research Coordinator — Workflow Simulation

## Why I built this
I'm working toward a Clinical Research Associate (CRA) role in Ireland and wanted to
understand REDCap-style clinical data management hands-on, not just read about it.
I don't yet have access to a live REDCap instance, so I rebuilt the core logic — 
data dictionaries, branching logic, calculated fields, validation, and safety 
monitoring — in Excel, formula by formula, to understand exactly how these systems work.

## What this project demonstrates
- Designing a REDCap-style data dictionary (field types, validation ranges,
  branching logic, identifiers, calculated fields)
- Simulating a CRC/CRA's daily workflow: data entry, quality control (QC) queries,
  clinical safety alerts, and end-of-day status reporting
- Debugging real data-integrity issues I introduced deliberately (see "What I got wrong" below)

## How I built it — and yes, I used AI to learn
I used Claude (Anthropic's AI) as a *tutor*, not a builder. It never wrote formulas
into my file for me — it explained concepts (e.g. why a calculated BMI field uses
`ROUND(weight/(height/100)^2,1)`, or what "branching logic" means in an EDC system),
and I typed every formula myself, tested it, and fixed it when it broke.
I'm including this openly because in clinical research, process transparency and
data integrity are the whole job — I'd rather show exactly how I learned this than
pretend I already knew it.

## What I got wrong (and fixed)
- Mixed up "typical/expected value range" with "data validation range" — a real
  design distinction in REDCap. Fixed by relabeling and documenting the difference.
- A COUNTIF formula silently counted 69 blank rows as "errors" because its range
  extended past my real data. Fixed by narrowing the range and matching exact text.
- [add any other real bug you hit and fixed]

## Workbook structure
1. `DATA_DICTIONARY` — field specifications (REDCap-style)
2. `Enrollment_Log` — participant data entry with live calculated fields
3. `QC_Query_Log` — automated data-quality checks (range + logic errors)
4. `Vital_Sign_Alerts` — clinical safety monitoring
5. `Daily_Status_Report` — auto-generated summary dashboard

## Data source
[Explain: illustrative/synthetic sample data generated to follow realistic
clinical ranges — not real patient data.]

## Regulatory context
This project reflects ICH-GCP E6(R2) principles around data quality, source data
verification, and query resolution — the same principles overseen in Ireland by
the HPRA (Health Products Regulatory Authority).

## Files in this repo
- 📊 [`Mock-Clinical-Trial-Data-Management.xlsx`](./Mock-Clinical-Trial-Data-Management.xlsx) —
  the full working workbook (open in Excel to see live formulas)
- 📋 [`REDCap_Data_Dictionary.csv`](./REDCap_Data_Dictionary.csv) —
  the data dictionary in REDCap's standard CSV export format (viewable directly on GitHub)
- 📄 [`Mock-Clinical-Trial-Data-Management.pdf`](https://github.com/nayana-doctor/clinical-data-management-simulation/blob/main/REDCap-style%20clinical%20data%20management%20workbook.pdf) —
  a quick-view snapshot of the workbook (viewable directly on GitHub, no download needed)
