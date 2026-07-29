--- 
title: France e-reporting (electronic reporting of transactions) implementation details
description: Learn implementation details of e-reporting in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# Data collection and classification for the French e-reporting

[!include [banner](../../includes/banner.md)]

This section describes how the **FR-eRep Populate Report Data** action collects source data for the French e-reporting report, how it filters each source transaction, and which section of the report the transaction is classified under. Use this information to reconcile the report content with the underlying subledger data (customer invoice journal, vendor invoice journal, project invoice journal, and tax transactions), and to understand why a specific transaction is included in, or excluded from, a specific report section.

Two different layers of the implementation enforce the selection and classification rules described in this section. They behave differently at run time:

- Hard-coded criteria are built into the source views, the union views, and the query initialization methods on the executable class. A functional user can't change these criteria at run time. To modify them, you need a code change or an extension.
- Configurable criteria are exposed as parameters on the `FR-eRep PopulateMessageItems` executable class that runs the **FR-eRep Populate Report Data** action. You can adjust these criteria per report section without a code change by editing the executable-class parameter values. Examples include the date field that is compared against the requested date range and any additional query filters that a customer or partner configures on the executable class for a specific report section.

In this topic, a gear (⚙) marks configurable criteria. A criterion that doesn't carry the gear is hard-coded. The configurable criteria (marked with ⚙) documented in this section reflect the default values that the [FR eReporting electronic messaging (EM) setup](emea-fra-e-reporting-preparation.md#data-entities) package ships. This behavior is what a user sees immediately after the setup package is imported and applied. If you modify a configurable criterion on the executable class after importing the setup package, the actual behavior for the affected report section deviates from what is documented here, and the company-specific configuration takes precedence.

The French e-reporting report contains two top-level report types (`TransactionsReportType`, `PaymentsReportType`), each split into two subsections that group source transactions by the type of counterparty relationship (business-to-business or business-to-consumer):

| Report type              | Subsection    | Scope | Typical rules that classify a source transaction under this subsection                                                                                             |
|--------------------------|---------------|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TransactionsReportType` | `Invoice`     | B2B   | The counterparty on the source invoice is an **Organization**⚙ and the **Delivery address** isn't **France**⚙.                                                       |
| `TransactionsReportType` | `Transaction` | B2C   | The counterparty on the source invoice is a **Person**⚙, or the source is a tax transaction that isn't linked to any invoice (see the rules for exact conditions). |
| `PaymentsReportType`     | `Invoice`     | B2B   | The counterparty on the settled source invoice is an **Organization**⚙ and the **Delivery address** isn't **France**⚙.                                               |
| `PaymentsReportType`     | `Transaction` | B2C   | The counterparty on the settled source invoice is a **Person**⚙, or the source is a conditional-tax transaction that isn't linked to any invoice (see the rules).  |

Apply common filters to every source transaction, regardless of the report type or subsection:

- Exclude reversals and reversed transactions.
- Consider only transactions that fall within the date range⚙ specified when the **FR-eRep Populate Report Data** action is executed.
- When evaluating the **Source** and **Origin** of a linked tax transaction, always exclude tax transactions with a **Source** of `Tax` (they're aggregate tax records, not source postings).

The rule-level bullets in the following subsections that state that a transaction must be *posted in the reporting period* refer to the configurable date range that is available in the parameters of the executable class.
The column labeled **Date range of reporting period** in the [Data selection matrix](#data-selection-matrix) shows which source-table date field is projected into the **Date** or **Closed date** column of the union view for each source entity.

## <a id="data-selection"></a>Data selection and classification rules

The following subsections describe the selection and classification rules for each report type and subsection. Each rule set lists the source journal, the counterparty and address criteria, and the linked tax transaction criteria that must be met for the source transaction to be included in the corresponding report section.

### `TransactionsReportType` – `Invoice` (B2B)

Select source transactions from the following journals. Classify these transactions under the **Invoice** subsection of the `TransactionsReportType`:

1. **Customer invoice journal** (including [Customer prepayment invoices](../../accounts-receivable/customer-prepayment-invoice.md))
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Project invoice journal** (including Project advance invoice)
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Vendor invoice journal**
   - Use linked tax transactions that have **Tax direction** set to either **Use Tax** or **Sales Tax Payable** with **Reverse charge** marker applied, and where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Vendor** is of type **Organization**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

### `TransactionsReportType` – `Transaction` (B2C)

Select source transactions from the following journals and tax transactions. Classify these transactions under the **Transaction** subsection of the `TransactionsReportType`:

1. **Customer invoice journal** (including [Customer prepayment invoices](../../accounts-receivable/customer-prepayment-invoice.md))
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Person**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Project invoice journal** (including Project advance invoice)
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Person**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Vendor invoice journal**
   - Use linked tax transactions that have **Tax direction** set to either **Use Tax** or **Sales Tax Payable** with **Reverse charge** marker applied, and where
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Vendor** is of type **Person**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Tax transactions**
   - That are either **Use Tax**, **Sales tax payable**, or **Tax-free sale**.
   - The **Source** of the tax transaction isn't **Tax**.
   - The **Origin** of the tax transaction isn't **Offset sales tax** or **Payment**.
   - Not linked to any invoice journal or **Customer prepayment invoice**.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.
     - If **Date of VAT register** is enabled in **General ledger parameters**, the **Date of VAT register** from the tax transaction is used instead of the tax transaction date as the criterion for selecting tax transactions by date when the **FR-eRep Populate Report Data** action is executed.

### `PaymentsReportType` – `Invoice` (B2B)

Select source transactions from the following journals and tax transactions. Classify these transactions under the **Invoice** subsection of the `PaymentsReportType`:

1. **Customer invoice journal** that represent [Customer prepayment invoices](../../accounts-receivable/customer-prepayment-invoice.md)
   - That are **fully** settled.
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Project invoice journal** that represent a Project advance invoice
   - That are **fully** settled.
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Tax transactions classified as conditional tax**
   - Linked to either a settled **Customer invoice journal** or a settled **Project invoice journal**.
   - The **Source** of the tax transaction isn't **Tax**.
   - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - The **Customer** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.

1. **Tax transactions classified as conditional tax**
   - That have **Tax direction** either **Use Tax**, or **Sales Tax Payable** with **Reverse charge** marker applied, and where:
     - The **Source** of the tax transaction isn't **Tax**.
     - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - Linked to a settled **Vendor invoice journal**.
   - The **Vendor** is of type **Organization**⚙.
   - The **Delivery address** isn't **France**⚙.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.

### `PaymentsReportType` – `Transaction` (B2C)

Select source transactions from the following journals and tax transactions. Classify these transactions under the **Transaction** subsection of the `PaymentsReportType`:

1. **Customer invoice journal** that represent [Customer prepayment invoices](../../accounts-receivable/customer-prepayment-invoice.md)
   - That are **fully** settled.
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Person**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Project invoice journal** that represent a Project advance invoice
   - That are **fully** settled.
   - With linked tax transactions where:
     - The **Source** of the linked tax transaction isn't **Tax**.
     - The **Origin** of the linked tax transaction isn't **Offset sales tax**.
   - The **Customer** is of type **Person**⚙.
   - Exclude reversals.
   - The transaction is posted in the **reporting period**⚙.

1. **Tax transactions classified as conditional tax**
   - Linked to either a settled **Customer invoice journal** or a settled **Project invoice journal**.
   - The **Source** of the tax transaction isn't **Tax**.
   - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - The **Customer** is of type **Person**⚙.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.

1. **Tax transactions classified as conditional tax**
   - That have **Tax direction** either **Use Tax**, or **Sales Tax Payable** with **Reverse charge** marker applied, and where:
     - The **Source** of the tax transaction isn't **Tax**.
     - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - Linked to a settled **Vendor invoice journal**.
   - The **Vendor** is of type **Person**⚙.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.

1. **Tax transactions classified as conditional tax**
   - That are either **Sales tax payable**, or **Tax-free sale**, and where:
     - The **Source** of the tax transaction isn't **Tax**.
     - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - **Not** linked to a **Customer invoice journal**, but linked to a settled **Customer transaction**.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.
     - If **Date of VAT register** is enabled in **General ledger parameters**, the **Date of VAT register** from the tax transaction is used instead of the tax transaction date as the criterion for selecting tax transactions by date when the **FR-eRep Populate Report Data** action is executed.

1. **Tax transactions classified as conditional tax**
   - That have **Tax direction** either **Use Tax**, or **Sales Tax Payable** with **Reverse charge** marker applied, and where:
     - The **Source** of the tax transaction isn't **Tax**.
     - The **Origin** of the tax transaction is **Payment** (conditional tax).
   - **Not** linked to a **Vendor invoice journal**, but linked to a settled **Vendor transaction**.
   - Exclude reversals.
   - Posted in the **reporting period**⚙.
     - If **Date of VAT register** is enabled in **General ledger parameters**, the **Date of VAT register** from the tax transaction is used instead of the tax transaction date as the criterion for selecting tax transactions by date when the **FR-eRep Populate Report Data** action is executed.

## <a id="data-selection-matrix"></a> Data selection matrix

The following matrix summarizes the selection criteria and the report classification for each source entity. It combines all selection rules from the previous subsections into a single reference table.

Legend:

- **NA** – The criterion isn't applicable to the source entity.
- **Not France** – The delivery address country or region is different from France.
- **Not Tax** – The value of the **Source** field on the linked tax transaction isn't **Tax**.
- **not Offset sales tax** – The value of the **Origin** field on the linked tax transaction isn't **Offset sales tax**.
- **Payment** – The value of the **Origin** field on the tax transaction is **Payment** (conditional tax).
- **Trans Date / Date of VAT register\*** – The tax transaction date is used, unless **Date of VAT register** is enabled in **General ledger parameters**, in which case the **Date of VAT register** is used.

| #  | **Entity**                              | **Message item type**            | Reversed | Date range of reporting period⚙     | Counterparty type⚙ | Delivery address⚙ | Fully settled | Settled with                         | Required linked tax transaction (Yes/No) | Required linked tax transaction (Tax direction) | Required linked tax transaction (Reverse charge) | Required linked tax transaction (Source) | Required linked tax transaction (Origin) | Report type / Subsection                 |
|----|-----------------------------------------|----------------------------------|----------|-------------------------------------|--------------------|-------------------|---------------|--------------------------------------|------------------------------------------|-------------------------------------------------|--------------------------------------------------|------------------------------------------|------------------------------------------|------------------------------------------|
| 1  | **Customer invoice journal**            | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | Not France        | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 2  | **Customer prepayment invoices**        | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | Not France        | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 3  | **Project invoice journal**             | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | Not France        | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 4  | **Project advance invoices**            | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | Not France        | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 5  | **Vendor invoice journal**              | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | NA                | NA            | NA                                   | Yes                                      | Use Tax                                         | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 6  | **Vendor invoice journal**              | **FR-eRep Transactions Invoice** | No       | Invoice Date                        | Organization       | NA                | NA            | NA                                   | Yes                                      | Sales Tax Payable                               | Yes                                              | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Invoice`     |
| 7  | **Customer invoice journal**            | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 8  | **Customer prepayment invoices**        | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 9  | **Project invoice journal**             | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 10 | **Project advance invoices**            | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 11 | **Vendor invoice journal**              | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | Use Tax                                         | NA                                               | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 12 | **Vendor invoice journal**              | **FR-eRep Transactions B2C**     | No       | Invoice Date                        | Person             | NA                | NA            | NA                                   | Yes                                      | Sales Tax Payable                               | Yes                                              | Not Tax                                  | not Offset sales tax                     | `TransactionsReportType` / `Transaction` |
| 13 | **Tax transaction**                     | **FR-eRep Transactions B2C**     | No       | Trans Date / Date of VAT register\* | NA                 | NA                | NA            | NA                                   | NA                                       | Use Tax / Sales tax payable / Tax-free sale     | NA                                               | Not Tax                                  | neither Offset Sales Tax nor Payment     | `TransactionsReportType` / `Transaction` |
| 14 | **Customer prepayment invoices**        | **FR-eRep Payments Invoice**     | No       | Settlement date                     | Organization       | Not France        | Yes           | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `PaymentsReportType` / `Invoice`         |
| 15 | **Project advance invoices**            | **FR-eRep Payments Invoice**     | No       | Settlement date                     | Organization       | Not France        | Yes           | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `PaymentsReportType` / `Invoice`         |
| 16 | **Tax transactions as conditional tax** | **FR-eRep Payments Invoice**     | No       | Trans Date                          | Organization       | Not France        | NA            | Cust / Proj Invoice journal          | NA                                       | NA                                              | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Invoice`         |
| 17 | **Tax transactions as conditional tax** | **FR-eRep Payments Invoice**     | No       | Trans Date                          | Organization       | Not France        | NA            | Vend Invoice journal                 | NA                                       | Use Tax                                         | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Invoice`         |
| 18 | **Tax transactions as conditional tax** | **FR-eRep Payments Invoice**     | No       | Trans Date                          | Organization       | Not France        | NA            | Vend Invoice journal                 | NA                                       | Sales Tax Payable                               | Yes                                              | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Invoice`         |
| 19 | **Customer prepayment invoices**        | **FR-eRep Payments B2C**         | No       | Settlement date                     | Person             | NA                | Yes           | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `PaymentsReportType` / `Transaction`     |
| 20 | **Project advance invoices**            | **FR-eRep Payments B2C**         | No       | Settlement date                     | Person             | NA                | Yes           | NA                                   | Yes                                      | NA                                              | NA                                               | Not Tax                                  | not Offset sales tax                     | `PaymentsReportType` / `Transaction`     |
| 21 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date                          | Person             | NA                | NA            | Cust / Proj Invoice journal          | NA                                       | NA                                              | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |
| 22 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date                          | Person             | NA                | NA            | Vend Invoice journal                 | NA                                       | Use Tax                                         | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |
| 23 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date                          | Person             | NA                | NA            | Vend Invoice journal                 | NA                                       | Sales Tax Payable                               | Yes                                              | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |
| 24 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date / Date of VAT register\* | NA                 | NA                | NA            | Customer transaction with no invoice | NA                                       | Sales tax payable / Tax-free sale               | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |
| 25 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date / Date of VAT register\* | NA                 | NA                | NA            | Vendor transaction with no invoice   | NA                                       | Use Tax                                         | NA                                               | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |
| 26 | **Tax transactions as conditional tax** | **FR-eRep Payments B2C**         | No       | Trans Date / Date of VAT register\* | NA                 | NA                | NA            | Vendor transaction with no invoice   | NA                                       | Sales Tax Payable                               | Yes                                              | Not Tax                                  | Payment                                  | `PaymentsReportType` / `Transaction`     |

\* If **Date of VAT register** is enabled in **General ledger parameters**, the **Date of VAT register** from the tax transaction is used instead of the tax transaction date as the criterion for selecting tax transactions by date when the **FR-eRep Populate Report Data** action is executed.

## Additional exclusions

Regardless of the report type or subsection, the **FR-eRep Populate Report Data** action applies the following additional exclusions to avoid double-counting:

- The action skips prepayment invoices that it reverses to the posted final invoice.
- The action skips project invoices that a corresponding free text invoice duplicates.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
