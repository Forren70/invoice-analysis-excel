# 🚀 CUSTOMER INVOICE ANALYSIS

This is a **Simulated Financial Analysis Workbook**. All names and data are completely fictitious and generated for demonstration purposes.

The project is structured to separate raw data from calculations. Analysis is based on a fixed reference date of **20/11/2025**.

## 1. 📄 Sheet: `Invoice_Master_Data`

**Role:** The main list of all invoices (Input Data). No formulas.

| Column | Description | Data Type |
| :--- | :--- | :--- |
| **Invoice Number** | Unique ID. | Number |
| **Issue Date** | Invoice creation date. | Date |
| **Customer** | Client name. | Text |
| **Amount** | Total transaction value. | Currency |
| **Due Date** | Payment deadline. | Date |
| **Payment Date** | Actual date payment was received (Manual input). Null if not yet paid. | Date |

![Screenshot 1 - Invoice_Master_Data Sheet Setup](assets/screenshot_1_invoice_master_data.png)

---

## 2. 📊 Sheet: `Analysis_Sheet`

**Role:** The work area for all calculations.

| Column | Description | Role |
| :--- | :--- | :--- |
| **A-F** | **Input Columns** | Copied from Master Data for tracing. (A-E are original inputs, F is Payment Date). |
| **G** | **Reference Date** | Fixed comparison date (20/11/2025). |
| **H** | **Calculated Status** | **FORMULA:** Shows if invoice is Paid, Overdue, or Unpaid. It prioritizes the Payment Date (F). |
| **I** | **Days Overdue** | **FORMULA:** Calculates days past due. |

![Screenshot 2 - Analysis_Sheet Setup](assets/screenshot_2_analysis_sheet.png)

---

## 3. 🧠 Calculation Logic: Calculated Status (Column H)

The core of the financial analysis lies in determining the status of each invoice, documented in the **Calculated Status (Column H)**. The formula used is:

`=IF(F2<>"","PAID",IF(E2<$G$2,"OVERDUE","UNPAID"))`

This formula prioritizes the transaction history over the deadline, operating in a hierarchy:

1.  **Paid Priority:** The system first checks the **Payment Date (Column F)**. If a date exists, the invoice is immediately marked as **PAID**. This status supersedes all other considerations, as the debt has been settled.
2.  **Overdue Check:** If the invoice has not been paid (i.e., Payment Date is null), the formula uses the fixed **Reference Date (Column G)** to check for delinquency. If the **Due Date (Column E)** is earlier than the Reference Date, the invoice is marked as **OVERDUE**.
3.  **Upaid Status:** If the invoice is neither PAID nor OVERDUE, it is marked as **UNPAID**. This means the payment is still expected, but the deadline has not yet been reached relative to the Reference Date.

---

## 4. ✨ Conditional Formatting

To provide a quick visual assessment of the invoice portfolio, Conditional Formatting is applied to the **Calculated Status (Column H)** using three simple rules:

| Condition | Rule | Formatting |
| :--- | :--- | :--- |
| Cell value is equal to `"PAID"` | `=H2="PAID"` | **Green** Fill (Completed transactions) |
| Cell value is equal to `"UNPAID"` | `=H2="UNPAID"` | **Yellow** Fill (Expected items, not yet due) |
| Cell value is equal to `"OVERDUE"` | `=H2="OVERDUE"` | **Red** Fill (Critical items, past due and unpaid) |

This visual system allows analysts to immediately identify critical items (Red), expected items (Yellow), and completed transactions (Green).

![Screenshot 3 - Analysis_Sheet Setup](assets/screenshot_3_conditional_formatting.png)

---

## 5. 🗓️ Days Overdue (Column I - Screenshot 4)

The **Days Overdue (Column I)** calculates the number of days a currently unpaid invoice is past its due date. This calculation only applies to invoices marked as **OVERDUE** in Column H.

The formula used is:

`=IF(H2="OVERDUE",$G$2-E2,0)`

* If the status in **Column H** is **OVERDUE**, the formula calculates the difference between the **Reference Date (G)** and the **Due Date (E)**.
* For all other statuses (PAID or UNPAID), the value is set to **0**, as the invoice is either settled or not yet due.

![Screenshot 4 - Analysis_Sheet Setup](assets/screenshot_4_days_overdue.png)