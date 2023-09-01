---

title: Business performance analytics data model
description: This article provides information about business performance analytics data model.
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
A businesss matrix is a roadmap for business data. Business data can be defined by value chains like record to report or order to cash. The business matrix organizes, connects, and simplifies data, helping users navigate and understand their data efficiently.

## Record to Report (R2R): 
This process encompasses the process from data collection to the final financial report. It ensures that business events are accurately recorded, processed, and summarized into financial statements and management reports.

| Business process  | Fact    | Grain    | Accounting Date Dim | CalendarDateDim | Reporting dimensions | Ledger | Reference Number | General ledger account | SubledgerNumber |
| ------------- | --------- | ---------- | ------------------- | --------------- | -------------------- | ------ | ---------------- | ---------------------- | --------------- |
| General Ledger transactions | GeneralLedgerFact| one row per account entry per ledger account | x       | x   | x   | x    | x    | x                      | x               |
| Budget transactions | BudgetFact | one row per account entry per ledger account |     | x               | x    | x   | x    | x                |                 |
| Budget reservation transactions | BudgetReservationFact | one row per reservation transaction  | x      |        | x  | x      | x             | x           |                 |

## Procure to Pay (P2P): 
This value chain covers the complete cycle from the procurement of goods and services to the payment of vendors. It's crucial for managing costs, ensuring timely payments, and maintaining good vendor relationships.

| Business process  | Fact   | Grain   | AccountingDateDim | Reporting Dimensions | DateDim | ProductDim | AssetDim | StorageLocationDim | PostalAddressDim | ReportingDimensionsDim | PartyDimDim | ProjectDim | NumberDim | LedgerDim | GeneralLedgerAccountDim2 | SubledgerNumberDim | BankAccountDim |
| -------- | ----- | ----- | ----- | --------- | ------- | ---------- | -------- | ------ | ----- | ---------- | -------- | ---------- | --------- | --------- | ----- | ---------- | -------------- |
| Purchase requisition  | PurchaseRequisitionFact | One row per requisition line   | x    | x   |  | x   | x | x  | x  | | x    | x     | x   | x   |                  |            |                |
| Purchase order |   |    |      |    |       |     |    |     |      |     |             |            |           |           |                                       |            |                |
|                      | PurchaseOrderFact | One row per PO line  | x    | x  |   | x<br>      | x   | x    | x     |      | x    | x    | x         | x      |        | x          |                |
| Product receipt      | ProductReceiptFact | One row per receipt line  | x  | x  |  | x   | x   | x  | x  |    | x  | | x         | x         |                      |             |                |
| Purchase invoices |  |   |    |    |    |    |     |     |         |     |             |            |           |           |                                       |             |                |
|                      | PurchaseInvoiceFact  | One row per invoice line item  | x  | x  | x  | x  | x  | x  | x  |   | x    | x          | x         | x         |     | x         |                |
| Purchase invoice matching | PurchaseInvoiceMatchingFact |One row per invoice line matched to PO| x | x | x | x | x | x |  |  | x  |  | x   | x         |          |               |                |
| Purchase payments | PurchasePaymentFact  | One row per payment | x  | x | x<br>   |   |   |  | x |   | x   |   | x     | x         |                   | x                        | x              |
| Purchase payment matching | PurchasePaymentMatchingFact | One row per payment matched to invoice| x | x  |  |  |   |   | x   |  | x  |   | x  | x    |   | x                      |                |
| Expense requisition | ExpenseRequisitionFact | One row per requisition line | x | x | | |  | | x  |  | x   | x      | x         |           |       |                             |                |
|  Expense report | ExpenseReportFact | One row per expense | x  | x   |   |   |  |   | x |  | x  | x   | x         | x         |              | x                                  |                |
| Purchase distribution  | PurchaseDistributionFact | One row per term  | x    | x  |  |  |  |  |  |   |     |    | x         | x         |    | x                                  |                |
| Purchase subledger    | PurchaseSubledgerFact     | One line per posted accounting event (voucher) | x | x | x  | |  | | x | x | x | x | | x |           | x                      |                |

## Order to Cash (O2C): 
This process involves receiving a customer order to collecting payment. It's vital for revenue management, customer satisfaction, and cash flow optimization.

| Business process | Fact   | Grain   | AccountingDateDim | BankAccountDim | LedgerDim | DateDim | NumberDim (RPD) | PartyDim | BuyingPartyDim | ProductDim | ProjectDim | PotalAddressDim | ReportingDimensionsDim | StorageLocationDim | SubledgerNumberDim | SalesCategory | WorkerDim | DeliveryModeDim |
| -------- | ----------- | ------- | ---------- | ------ | --------- | ------- | - | ----- | ----- | ---------- | ---------- | ------- | ------ | ------- | ---- | ------------- | --------- | ----------- |
| Sales order | SalesOrderFact  | One row per sales order line  |   |   | x  |   | x  | x  | x    | x    | x   | x    | x      | x     | x                  |               |           |                 |
| Service order | ServiceOrderFact | One row per sales order line |  |  | x  |   | x  |    | x    | x    | x   | x    | x      |       | x                  |               | x         |                 |
| Picking slip  | PickingSlipFact | One row per item picked   |      |  | x  |   | x  |    | x    | x    |     |      |        | x     |                    |               | x         | x               |
| Packing slip  | PackingSlipFact | One row per item on packing slip | x | | x | | x  |    | x    | x    |     | x    |        | x     | x                  | x             |           | x               |
| Sales contract billing | SalesContractBillingFact| One row per sales billing line per contract period | | | x | | x | | x | x | x | | x  | x  |           |               |           |                 |
| Deferred revenue| DeferredRevenueFact | One row per revenue line billed per contract period | x | | x |  |  |   |   |   |  |   |  |  |                    |               |           |                 |
| Sales invoice | SalesInvoiceFact | One row per sales invoice line | x | | x | | x | | x | x | x | x |           | x                  | x                  | x             |           |                 |
| Sales returns | SalesReturnsFact | One row per order line returned|   | | x | | x | | x | x |   | x |           | x                  |                    | x             |           |                 |
| Sales payments| SalesPaymentFact | One row per payment          | x | x | x | | x | x | x |  |  | x | x         |                    | x                  |               |           |                 |
| Sales payments matching | SalesPaymentMatchingFact | One row per payment matched to invoice| x | | x | | x |    | x     |   |   | x  |    |  | x          |               |           |                 |
| Sales subledger| SalesSubledgerFact| One row per posted accounting event (voucher)       | x   | | x | |   |    | x     |   |   | x  | x  |  | x          |               |           |                 |
| Sales distribution| SalesDistributionFact  | One row per term                            |     | |   | |   |    |       |   |   |    |    |  |            |               |           |                 |
| Bank reconciliation | BankRegisterFact     | One row per bank transaction                | x | x | x | | x |    |       |   |   |    |    |  | x          |               |           |                 |
| Bank reconciliation| BankStatementFact     | One row per bank statement transaction      |   | x | x | | x |    |       |   |   |    |    |  | x          |               |           |                 |
