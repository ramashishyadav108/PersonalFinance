# Personal Finance – Power BI Dashboard

A simple, end-to-end Personal Finance dashboard built in **Power BI**.  
It helps you track income, expenses, savings and spending patterns using a single Excel workbook as the data source.

> Inspired by the Codebasics personal finance project on YouTube.

---

## ✨ Features

- Income vs Expense overview with monthly trends
- Category-wise spending breakdown (top categories)
- Savings & balance KPIs
- Month / Year / Account filters (slicers)
- Clean, beginner-friendly Power BI file structure

> This repo stores the **decomposed Power BI project** (source-controlled files) instead of a single `.pbix` file.

---

## 🗂️ Repository Structure

```
PersonalFinance/
├─ Report/              # Report layout & visuals
├─ DataModel/           # Model metadata (tables, relationships, measures)
├─ DiagramLayout/       # Model diagram positions
├─ Metadata/            # Project metadata
├─ SecurityBindings/    # Security bindings (if any)
├─ Settings/            # Project settings
├─ Version/             # Version info
├─ [Content_Types].xml  # Package content map
└─ FinanceDatabase.xlsx # Sample data source (Excel)
```

---

## 🚀 Getting Started

You have **two** easy ways to run this project.

### Option A) Open as a Power BI *Project* (recommended if using PBIP)

> Requires Power BI Desktop with **Project (PBIP)** support enabled (Preview feature).

1. Open **Power BI Desktop** (latest).
2. Go to **File → Options and settings → Options → Preview features** and ensure **Power BI Project (.pbip)** is enabled.
3. If a `.pbip` file exists in the repo, open it via **File → Open → Project** and select the `.pbip`.
4. When prompted, fix the Excel file path to `FinanceDatabase.xlsx` (see “Update data source” below) and **Refresh**.

> If there is no `.pbip` in this repo, use **Option B**.

### Option B) Compile to a reusable file and open in Desktop

If you prefer a single file to open:

**B1. Build a `.pbit` (template) using `pbi-tools`**
1. Install .NET 6+ and the `pbi-tools` CLI.
2. From a terminal in the repo root, run:

   ```bash
   # Install pbi-tools (one time)
   dotnet tool install -g pbi.tools

   # Compile this project into a Power BI Template (.pbit)
   pbi-tools compile . -format PBIT -outPath PersonalFinance.pbit
   ```

3. Open `PersonalFinance.pbit` in Power BI Desktop, point it to `FinanceDatabase.xlsx`, and **Load**.

> `.pbix` compilation is supported by pbi-tools mainly for **report-only (thin)** files. For projects that include a data model (like this), generate a **.pbit** and hydrate it in Desktop.

---

## 🔄 Update the data source (Excel)

The sample data is in `FinanceDatabase.xlsx` at the repo root.

1. In Power BI Desktop, click **Transform data → Data source settings**.
2. Select the Excel source → **Change Source…**.
3. Browse to your local path of `FinanceDatabase.xlsx` and confirm.
4. Click **Close & Apply** and then **Refresh**.

> Tip: Keep your Excel columns consistent (e.g., `Date`, `Type` (Income/Expense), `Category`, `Description`, `Amount`, `Account`). You can add more columns; just update the model accordingly.

---

## 📊 Measures (examples)

You can adapt these as needed:

```DAX
Total Expense = SUMX(FILTER(Transactions, Transactions[Type] = "Expense"), Transactions[Amount])
Total Income  = SUMX(FILTER(Transactions, Transactions[Type] = "Income"),  Transactions[Amount])
Balance       = [Total Income] - [Total Expense]
Savings %     = DIVIDE([Balance], [Total Income])
```

> Replace `Transactions` and column names with the actual table/columns in your model.

---

## 🧪 What to explore

- Add Year/Month slicers
- Create a “Top N categories” visual
- Build a monthly trend line for Income vs Expense
- Add bookmarks for “Overview”, “Categories”, “Transactions”

---

## 🙏 Credits

- Project idea & walkthrough: Codebasics – *Personal Finance Dashboard in Power BI* (YouTube)
- Thanks to the Power BI community for PBIP & source-control best practices




