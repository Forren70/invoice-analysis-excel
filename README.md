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

![Screenshot 1 - Invoice_Master_Data Sheet Setup](assets/screenshot_1_invoice_master_data.png)

---

## 2. 📊 Sheet: `Analysis_Sheet`

**Role:** The work area for all calculations.

| Column | Description | Role |
| :--- | :--- | :--- |
| **A-E** | **Input Columns** | Copied from Master Data for tracing. |
| **F** | **Reference Date** | Fixed comparison date (20/11/2025). |
| **G** | **Calculated Status** | **FORMULA:** Shows if invoice is Overdue or Unpaid. |
| **H** | **Days Overdue** | **FORMULA:** Calculates days past due. |

![Screenshot 2 - Analysis_Sheet Setup](assets/screenshot_2_analysis_sheet.png)