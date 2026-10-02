# USGS 16518000 — West Wailuaiki Stream near Keanae, Maui, HI

| File | What it holds |
|---|---|
| `daily-discharge.rdb` | Daily mean discharge (ft³/s), 1914-01-01 to 2026-09-30, unchanged from USGS |
| `annual-mean-flow.csv` | Mean of the daily values per water year (Oct–Sep), with the number of days behind each |
| `annual-mean-flow.xlsx` | The same yearly means in Excel, with the trend (SLOPE) and 30-year averages as formulas, and a Source sheet |

**Source:** U.S. Geological Survey, National Water Information System, daily
values, parameter 00060 (discharge), statistic 00003 (mean).
`https://waterservices.usgs.gov/nwis/dv/?sites=16518000&parameterCd=00060&startDT=1900-01-01&format=rdb`

**Retrieved:** 2026-10-02 by Cori Mackie (the file's own header records
03:39 Eastern).

**Notes**

- Missing: 1916-01-01 to 1916-05-31 and 1917-09-30 to 1921-10-31.
  Water years 1918–1921 have no data and are absent from the CSV. Water
  years 1914 and 1916 have under 90% of their days, are marked
  `complete = False`, and are left out of any trend. That leaves 107
  complete water years.
- 77 days at the end of the record are provisional (code `P`); 227 are
  USGS estimates (`A:e`).
- The gauge is at 1,550 ft, above the Koolau Ditch, so it measures flow
  before diversion (CWRM Instream Flow Standard Assessment Report
  PR-2009-08; confirm in the report before citing).
