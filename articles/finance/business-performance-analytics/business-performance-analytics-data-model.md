---

title: Business performance analytics data model
description: This article provides information about the business performance analytics data model.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 08/31/2023
ms.topic: data model
ms.prod: 
ms.technology:
ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
---

# Business performance analytics data model

A business matrix is a roadmap for business data. Business data can be defined by value chains such as *record to report* or *order to cash*. The business matrix organizes, connects, and simplifies data. In this way, it helps users efficiently navigate and understand their data.

## Record to report

*Record to report* covers the process from data collection through the final financial report. It ensures that business events are accurately recorded, processed, and summarized into financial statements and management reports.

| Business process                | Fact                  | Grain                                      | Accounting Date | Ledger | Reference Number | General ledger account | SubledgerNumber |
| ------------------------------- | --------------------- | ------------------------------------------ | --------------- | ------ | ---------------- | ---------------------- | --------------- |
| General Ledger Transactions     | GeneralLedgerFact     | 1 row per account entry per ledger account | x               | x      | x                | x                      | x               |
| Budget transactions             | BudgetFact            | 1 row per account entry per ledger account |                 | x      | x                | x                      |                 |
| Budget reservation transactions | BudgetReservationFact | 1 row per reservation transaction          | x               | x      | x                | x                      |                 |

## Procure to pay

*Procure to pay* covers the complete cycle from the procurement of goods and services through the payment of vendors. It's crucial for managing costs, ensuring timely payments, and maintaining good vendor relationships.

| Business process | Fact | Grain | AccountingDateDim | Reporting Dimensions | DateDim | ProductDim | AssetDim | StorageLocationDim | PostalAddressDim | ReportingDimensionsDim | PartyDimDim | ProjectDim | NumberDim | LedgerDim | GeneralLedgerAccountDim2 | SubledgerNumberDim | BankAccountDim |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Purchase requisition | PurchaseRequisitionFact | One row per requisition line | X |   | | X | X | X | X | | X | X | X | X | | | |
| Purchase order | | | | | | | | | | | | | | | | | |
| | PurchaseOrderFact | One row per purchase order (PO) line | X |   | | X | X | X | X | | X | X | X | X | | X | |
| Product receipt | ProductReceiptFact | One row per receipt line | X |   | | X | X | X | X | | X | | X | X | | | |
| Purchase invoices | | | | | | | | | | | | | | | | | |
| | PurchaseInvoiceFact | One row per invoice line item | X |   | X | X | X | X | X | | X | X | X | X | | X | |
| Purchase invoice matching | PurchaseInvoiceMatchingFact | One row per invoice line that's matched to a PO | X |   | X | X | X | X | | | X | | X | X | | | |
| Purchase payments | PurchasePaymentFact | One row per payment | X |   | X | | | | X | | X | | X | X | | X | X |
| Purchase payment matching | PurchasePaymentMatchingFact | One row per payment that's matched to an invoice | X |  | | | | | X | | X | | X | X | | X | |
| Expense requisition | ExpenseRequisitionFact | One row per requisition line | X |  | | | | | X | | X | X | X | | | | |
| Expense report | ExpenseReportFact | One row per expense | X |  | | | | | X | | X | X | X | X | | X | |
| Purchase distribution | PurchaseDistributionFact | One row per term | X | X | | | | | | | | | X | X | | X | |
| Purchase subledger | PurchaseSubledgerFact | One line per posted accounting event (voucher) | X | X | X | | | | X | X | X | X | | X | | X | |

## Order to cash

*Order to cash* covers the process from the receipt of a customer order through payment collection. It's crucial for managing revenue, ensuring customer satisfaction, and optimizing cash flow.

| Business process        | Fact                     | Grain                                             | AccountingDateDim | BankAccountDim | LedgerDim | DateDim | NumberDim (RPD) | PartyDim | BuyingPartyDim | ProductDim | ProjectDim | PotalAddressDim | ReportingDimensionsDim | StorageLocationDim | SubledgerNumberDim | SalesCategory | WorkerDim | DeliveryModeDim |
| ----------------------- | ------------------------ | ------------------------------------------------- | ----------------- | -------------- | --------- | ------- | --------------- | -------- | -------------- | ---------- | ---------- | --------------- | ---------------------- | ------------------ | ------------------ | ------------- | --------- | --------------- |
| Sales Order             | SalesOrderFact           | 1 row per sales order line                        |                   |                | x         |         | x               | x        | x              | x          | x          | x               |                        | x                  | x                  |               |           |                 |
| Service Order           | ServiceOrderFact         | 1 row per sales order line                        |                   |                | x         |         | x               |          | x              | x          | x          | x               |                        |                    | x                  |               | x         |                 |
| Picking Slip            | PickingSlipFact          | 1 row per item picked                             |                   |                | x         |         | x               |          | x              | x          |            |                 |                        | x                  |                    |               | x         | x               |
| Packing Slip            | PackingSlipFact          | 1 row per item on packing slip                    | x                 |                | x         |         | x               |          | x              | x          |            | x               |                        | x                  | x                  | x             |           | x               |
| Sales Contract Billing  | SalesContractBillingFact | 1 row per sales billing  line per contract period |                   |                | x         |         | x               |          | x              | x          | x          |                 |                        | x                  |                    |               |           |                 |
| Deferred Revenue        | DeferredRevenueFact      | 1 row per revenue line billed per contract period | x                 |                | x         |         |                 |          |                |            |            |                 |                        |                    |                    |               |           |                 |
| Sales Invoice           | SalesInvoiceFact         | 1 row per Sales Invoice line                      | x                 |                | x         |         | x               |          | x              | x          | x          | x               |                        | x                  | x                  | x             |           |                 |
| Sales Returns           | SalesReturnsFact         | 1 row per order line returned                     |                   |                | x         |         | x               |          | x              | x          |            | x               |                        | x                  |                    | x             |           |                 |
| Sales Payments          | SalesPaymentFact         | 1 row per payment                                 | x                 | x              | x         |         | x               | x        | x              |            |            | x               |                        |                    | x                  |               |           |                 |
| Sales Payments Matching | SalesPaymentMatchingFact | 1 row per payment matched to invoice              | x                 |                | x         |         | x               |          | x              |            |            | x               |                        |                    | x                  |               |           |                 |
| Sales Subledger         | SalesSubledgerFact       | 1 row per posted accounting event (voucher)       | x                 |                | x         |         |                 |          | x              |            |            | x               | x                      |                    | x                  |               |           |                 |
| Sales Distribution      | SalesDistributionFact    | 1 row per term                                    |                   |                |           |         |                 |          |                |            |            |                 | x                      |                    |                    |               |           |                 |
| Bank Reconciliation     | BankRegisterFact         | 1 row per bank transaction                        | x                 | x              | x         |         | x               |          |                |            |            |                 |                        |                    | x                  |               |           |                 |
| Bank Reconciliation     | BankStatementFact        | 1 row per bank statement transaction              |                   | x              | x         |         | x               |          |                |            |            |                 |                        |                    | x                  |               |           |                 |
