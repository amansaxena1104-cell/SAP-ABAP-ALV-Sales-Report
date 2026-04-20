# SAP ABAP R2R (Record-to-Report) Project

This project implements a complete SAP ABAP Record-to-Report (R2R) solution for ABC Distribution Ltd., providing comprehensive financial reporting and period close functionality.

---

## Project Structure

```
src/
├── programs/
│   ├── ZFIR001.abap          # Main R2R Period Close Dashboard
│   ├── ZFIR003.abap          # Trial Balance ALV Report
│   ├── ZFIR004.abap          # AR/AP Aging Report
│   ├── ZFIR004.abap          # Bank Reconciliation Report
│
├── includes/
│   ├── ZFIR001_TOP.abap      # Global declarations
│   ├── ZFIR001_SEL.abap      # Selection screen
│   ├── ZFIR001_FORMS.abap    # FORM routines
│   ├── ZFIR001_ALV.abap      # ALV display routines
│
├── function_groups/
│   ├── ZFIR_UTILS/
│   │   ├── ZFIR_FORMAT_AMOUNT.abap
│   │   ├── ZFIR_VALIDATE_PERIOD.abap
│   │   ├── ZFIR_GET_NEXT_PERIOD.abap
│
├── structures/
│   ├── ZFIR_S_TB_LINE.txt    # Trial Balance structure
│   ├── ZFIR_S_AGING.txt      # AR/AP aging structure
│   ├── ZFIR_S_RECON.txt      # Reconciliation structure
│
├── table_types/
│   ├── ZFIR_T_TB_LINE.txt
│   ├── ZFIR_T_AGING.txt
│   ├── ZFIR_T_RECON.txt
│
├── data_elements/
│   ├── ZFIR_BUKRS.txt
│   ├── ZFIR_GJAHR.txt
│   ├── ZFIR_MONAT.txt
│
├── message_class/
│   ├── ZFIR_MAK.txt
│
└── ZFIR_TEST_DATA.abap       # Test data creation script
```

---

## Key Features

### ZFIR001 - Main Dashboard
- **Trial Balance:** GL account balances with variance analysis
- **AR Aging:** Accounts receivable balances bucketed by aging periods
- **AP Aging:** Vendor payables bucketed by aging periods
- **Reconciliation Status:** GL vs sub-ledger reconciliation
- **Period Close Checklist:** 16-step month-end and close process

---

### ZFIR003 - Trial Balance Report
- Standalone trial balance with filtering options
- Variance analysis against previous periods
- Alert flags for significant variances

---

### ZFIR003 - AR/AP Aging Report
- Aging analysis for receivables and payables
- Risk flagging for overdue items (>90 days)
- Customer/Vendor name resolution

---

### ZFIR004 - Bank Reconciliation
- GL balance vs bank statement reconciliation
- Outstanding items tracking
- Deposits in transit and outstanding checks

---

## SAP Objects to Create

| Object Type | Object Name | Description |
|---|---|---|
| Structure | ZFIR_S_TB_LINE | Trial Balance Line Structure |
| Structure | ZFIR_S_AGING | AR/AP Aging Structure |
| Structure | ZFIR_S_RECON | Reconciliation Structure |
| Table Type | ZFIR_T_TB_LINE | Trial Balance Table Type |
| Table Type | ZFIR_T_AGING | Aging Table Type |
| Table Type | ZFIR_T_RECON | Reconciliation Table Type |
| Data Element | ZFIR_BUKRS | Company Code Element |
| Data Element | ZFIR_GJAHR | Fiscal Year Element |
| Data Element | ZFIR_MONAT | Fiscal Period Element |
| Message Class | ZFIR_MAK | R2R Message Class |

---

## Tech Stack

- **SAP ECC 6.0 / S/4HANA**
- **ABAP Release:** 7.50+
- **Transactions:** SE38, SE11, SE37, SM30
- **ALV:** REUSE_ALV_GRID_DISPLAY
- **SAP Tables:** GLT0, BSEG, BKPF, KNA1, LFA1, BSAD, BSAK, FEBEP

---

## How to Install

1. Create all **Data Dictionary** objects first (structures, table types, data elements, message class)
2. Create **Function Group** ZFIR_UTILS and add the three function modules
3. Create **Include programs** (TOP, SEL, FORMS, ALV)
4. Create and activate **main programs** ZFIR001, ZFIR003, ZFIR004
5. Run **ZFIR_TEST_DATA** to populate test data
6. Execute ZFIR001 via SE38 or assign to a transaction code

---

## Execution

```
Transaction: SE38
Program:     ZFIR001   → Main R2R Dashboard
Program:     ZFIR003   → Trial Balance Report
Program:     ZFIR003   → AR/AP Aging Report
Program:     ZFIR004   → Bank Reconciliation Report
```

---

## Future Enhancements

- SAP Fiori launchpad integration
- Automated period-close workflow with email notifications
- Integration with SAP Financial Closing Cockpit
- PDF export of period-close checklist
- Authorization object checks per company code

---

## Author

**Aman Saxena**
Roll No: 23053187
Batch: 2027 (CSE)
Specialization: SAP ABAP Development
