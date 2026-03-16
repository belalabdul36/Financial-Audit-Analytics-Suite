# Financial-Audit-Analytics-Suite

Automated financial analysis and audit workflows built in Alteryx Designer, using real-world accounting datasets including General Ledger, Accounts Receivable, Accounts Payable, and Bank Statement data.

## Workflows

### 1. Bank Reconciliation
Joins GL export and bank statement data on transaction IDs to automatically isolate unrecorded items. Unmatched transactions are categorized using a Formula tool (Bank Charges, Transfer Fees, Bank Income, etc.) and exported as an exceptions report.

**Tools used:** Input, Select, Join, Formula, Output  
**Output:** `Reconciling_Items.xlsx` — 18 unmatched transactions flagged for review

### 2. AR/AP Aging Analysis
Calculates days outstanding for each invoice using `DateTimeDiff`, buckets them into aging categories (Current, 30-60, 60-90, 90+ days), and summarizes total amounts and invoice counts per bucket.

**Tools used:** Input, Select, Formula, Summarize, Output  
**Output:** `AR_AP_Aging_Report.xlsx` — two-tab Excel report covering 1,700+ invoices

### 3. GL Department Spend Analysis
Summarizes General Ledger data by department to identify total debit and credit activity across cost centres.

**Tools used:** Input, Select, Summarize, Sort, Output  
**Output:** Ranked department spend report

## Tools & Skills Demonstrated
- Alteryx Designer (Core + Advanced)
- DateTimeDiff, CONTAINS, IF/ELSEIF expressions
- Join (inner, left, right unmatched outputs)
- Data type conversion and cleansing
- Multi-sheet Excel output

## Data
Sample datasets generated for portfolio purposes, modelled after real accounting data structures (GL, AR, AP, Bank Statement).
