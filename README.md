# Financial Audit & Analytics Suite

> Automated AR/AP aging analysis built in Alteryx Designer — turns raw invoice data into a structured aging report in seconds, no Excel formulas, no manual work.

---

## What It Does

Most accountants spend hours manually categorizing invoices, calculating days outstanding, and building aging reports every month. This workflow does it in one click.

**Input:** Two raw Excel files — Accounts Receivable and Accounts Payable  
**Output:** A two-tab Excel report bucketing every invoice by how overdue it is

| Aging Bucket | AR Amount | AR Invoices | AP Amount | AP Invoices |
|---|---|---|---|---|
| Current (0-30 days) | $1,720,999 | 225 | $2,071,132 | 200 |
| 30-60 Days | $1,363,780 | 180 | $1,911,700 | 200 |
| 60-90 Days | $1,439,083 | 180 | $2,056,514 | 200 |
| 90+ Days | $2,322,964 | 315 | $1,868,216 | 200 |
| **Total** | **$6,846,826** | **900** | **$7,907,562** | **800** |

---

## Workflow

Built entirely in Alteryx Designer with no code — just logic.
```
Input (AR/AP Excel)
  → Select        [fix data types]
  → Formula 1     [DateTimeDiff(DateTimeToday(), [InvoiceDate], "days") → Days_Outstanding]
  → Formula 2     [IF/ELSEIF bucket logic → Aging_Bucket]
  → Summarize     [Group By Aging_Bucket, Sum Amount, Count invoices]
  → Output        [Two-tab Excel: AR sheet + AP sheet]
```

**Key Alteryx tools used:** Input Data, Select, Formula, Summarize, Output Data

**Key expressions:**
```
Days_Outstanding = DateTimeDiff(DateTimeToday(), [InvoiceDate], "days")

Aging_Bucket =
  IF [Days_Outstanding] <= 30 THEN "Current (0-30)"
  ELSEIF [Days_Outstanding] <= 60 THEN "30-60 Days"
  ELSEIF [Days_Outstanding] <= 90 THEN "60-90 Days"
  ELSE "90+ Days"
  ENDIF
```

---

## Files

| File | Description |
|---|---|
| `Alteryx GitHub.yxmd` | The Alteryx workflow — open in Alteryx Designer and run |
| `Accounts-Receivable CLAUDE.xlsx` | AR input data (900 invoices) |
| `Accounts-Payable CLAUDE.xlsx` | AP input data (800 invoices) |
| `Account Receivable ^0 Payable ALT.xlsx` | Final output — two-tab aging report |

---

## How To Run

1. Download all files
2. Open `Alteryx GitHub.yxmd` in Alteryx Designer
3. Update the Input Data file paths to wherever you saved the Excel files
4. Hit Run
5. Output writes to the same folder

---

## Skills Demonstrated

`Alteryx Designer` `DateTimeDiff` `IF/ELSEIF Logic` `Data Type Conversion` `Summarize` `Multi-Sheet Excel Output` `Accounts Receivable` `Accounts Payable` `Aging Analysis` `Financial Reporting`
