# USGS 16518000 — West Wailuaiki Stream near Keanae, Maui, HI

| File | What it holds |
|---|---|
| `daily-discharge.rdb` | Daily mean discharge (ft³/s), 1914-01-01 to 2026-09-30, unchanged from USGS |
| `annual-mean-flow.csv` | Mean of the daily values per water year (Oct–Sep), with the number of days behind each |

**Source:** U.S. Geological Survey, National Water Information System, daily
values, parameter 00060 (discharge), statistic 00003 (mean).
`https://waterservices.usgs.gov/nwis/dv/?sites=16518000&parameterCd=00060&startDT=1900-01-01&format=rdb`

**Retrieved:** 2026-10-02 by Cori Mackie (the file's own header records
03:39 Eastern).

**Notes**

- Missing: 1916-01-01 to 1916-05-31 and 1917-09-30 to 1921-10-31.
  Water years with under 90% of their days (1914, 1916–1921 partial) are
  marked `complete = False` and are left out of any trend.
- 77 days at the end of the record are provisional (code `P`); 227 are
  USGS estimates (`A:e`).
- Not yet checked: whether this gauge sits above or below the East Maui
  ditch intakes, which decides whether it measures natural flow or flow
  left after diversion.
