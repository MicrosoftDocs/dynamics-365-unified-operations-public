---

title: Business performance analytics data model
description: This article provides information about the business performance analytics data model.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 11/29/2023
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

| Business process                | Fact                  | Grain                                      | Accounting date | Ledger | Reference number | General ledger account | SubledgerNumber |
| ------------------------------- | --------------------- | ------------------------------------------ | --------------- | ------ | ---------------- | ---------------------- | --------------- |
| General ledger transactions     | GeneralLedgerFact     | One row per account entry per ledger account | x               | x      | x                | x                      | x               |
| Budget transactions             | BudgetFact            | One row per account entry per ledger account |                 | x      | x                | x                      |                 |
| Budget reservation transactions | BudgetReservationFact | One row per reservation transaction          | x               | x      | x                | x                      |                 |

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

| Business process   | Fact     | Grain    | AccountingDateDim | BankAccountDim | LedgerDim | DateDim | NumberDim (RPD) | PartyDim | BuyingPartyDim | ProductDim | ProjectDim | PotalAddressDim | ReportingDimensionsDim | StorageLocationDim | SubledgerNumberDim | SalesCategory | WorkerDim | DeliveryModeDim |
| ------- | ------ | -------- | ----- | ------ | ----- | ------- | --- | -------- | ----- | ---------- | ---------- | --------------- | ---------- | ------- | -----| ------------ | --------- | --------------- |
| Sales order  | SalesOrderFact    | One row per sales order line   |   |  | X  |    | X   | X  | X    | X   | X  | X   |      | X      | X                  |               |           |                 |
| Service order | ServiceOrderFact | One row per sales order line   |  |   | X  |    | X   |   | X  | X   | X | X |   |      | X                  |               | X         |                 |
| Picking slip  | PickingSlipFact  | One row per item picked       |   |   | X  |    | X   |  | X  | X   |   |     |        | X                  |             |               | X         | X               |
| Packing slip  | PackingSlipFact  | One row per item on packing slip | X | | X |  | X  |    | X  | X  |   | X  |     | X                  | X                  | X         |           | X               |
| Sales contract billing  | SalesContractBillingFact | One row per sales billing line per contract period | |  |X  | | X | | X | X | X  |   |  | X  |      |               |           |                 |
| Deferred revenue  | DeferredRevenueFact  | One row per revenue line billed per contract period | X | | X |  |  |  |  |  |  |  |   |     |                    |               |           |                 |
| Sales invoice | SalesInvoiceFact | One row per sales invoice line | X |  | X | | X |  | X | X | X  | X   |        | X                  | X               | X             |           |                 |
| Sales returns  | SalesReturnsFact  | One row per order line returned | | | X |  | X |  | X | X    |     | X   |       | X                  |                    | X             |           |                 |
| Sales payments | SalesPaymentFact  | One row per payment  | X | X  | X |  | X | X  | X |  |   | X  |   |                    | X                  |               |           |                 |
| Sales payments matching | SalesPaymentMatchingFact | One row per payment matched to invoice | X | | X | |X  | | X |  |  | X | |  | X              |               |           |                 |
| Sales subledger  | SalesSubledgerFact | One row per posted accounting event (voucher) | X |  | X  |   |   |   | X |  |  | X | X  |     | X        |               |           |                 |
| Sales distribution | SalesDistributionFact | One row per term |  |   |   |   |    |    |     |     |    |     | X      |       |                    |               |           |                 |
| Bank reconciliation | BankRegisterFact  | One row per bank transaction | X  | X | X  |  | X |  |    |   |     |     |         |        | X                  |               |           |                 |
| Bank reconciliation | BankStatementFact | One row per bank statement transaction | | X |X  |  | X | |   |    |    |   |   |     | X              |               |           |                 |
