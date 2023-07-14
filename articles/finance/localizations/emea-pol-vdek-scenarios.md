---
title: Details of specific business scenarios in the JPK-V7 report
description: This article explains details of specific business scenarios in the JPK-V7 report in Poland.
author: liza-golub
ms.date: 07/19/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Poland
ms.author: egolub
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
---

# Details of specific business scenarios in the JPK-V7 report

[!include [banner](../includes/banner.md)]

This article explains details of specific business scenarios in the JPK-V7 report in Poland.

## Reporting of overdue customer invoices

JPK-V7 report in Microsoft Dynamics 365 Finance supports reporting of overdue customer invoices when the local Polish [Overdue debt VAT](emea-pol-sales-tax-reports.md#allowance-for-bad-debts) feature is used.

### Business requirement

- If the procedure is applied by the company, the **\<P_68\>** element of the declaration part must report the amount of the taxable base for overdue invoices in the reporting period (that is, transactions that are posted to deduct value-added tax (VAT) for issued invoices that aren't paid within 150 days after the payment due date).
- If the procedure is applied by the company, the **\<P_69\>** element of the declaration part must report the amount of VAT for overdue invoices in the reporting period (that is, transactions that are posted to deduct VAT for issued invoices that aren't paid within 150 days after the payment due date).
- If the procedure is applied by the company, for overdue invoices in the period where the due date is 150 days, this transaction must be reported. Information about the customer from the original invoice and an amount that has a minus sign (–) must be included.
- If the procedure is applied by the company, for paid overdue invoices in the period when an overdue invoice was paid, this transaction must be reported. All the information about the customer from the original invoice and an amount that has a plus sign (+) must be included.
- If the procedure is applied by the company, and if overdue and paid overdue transactions are in the same reporting period, you can optionally report both transactions together in the sales register. In this case, the **\<P_68\>** and **\<P_69\>** elements of the declaration part aren't reported.

### Supported business user scenario in Finance

When there is an overdue customer invoice, the invoice that is issued to a customer can go through three stages:

1. The invoice is issued to the customer, tax transactions are posted, and the invoice is included in **JPK** > **Ewidencja** > **SprzedazWiersz** as usual, according to the tax setup and marker setup.
2. If the invoice isn't paid within 150 days after the payment due date, the company can apply the [Overdue debt VAT](emea-pol-sales-tax-reports.md#allowance-for-bad-debts) periodic task by going to **Accounts receivable** > **Periodic tasks** > **Overdue debt VAT**. Tax transactions that are produced by this task are reflected in the JPK-V7M report. The following information is included:

    - All the customer information from the original invoice that was posted in stage 1 is included.
    - Amounts are reported in the same **K_\*** elements as in the original invoice, but they have a negative sign.
    - The same markers that were applied in the original invoice are applied.
    - The **\<KorektaPodstawyOpodt\>** marker is applied.

    Moreover, the base amount and tax amount from this invoice (internal document) are included and reported in the **P_68** and **P_69** elements of the declaration part of the report.

3. If the invoice is paid after both stage 1 and stage 2 have occurred, the company must again apply the **Overdue debt VAT** periodic task in the period when the invoice was paid. The resulting tax transactions are reflected in the JPK-V7 report. The following information is included:

    - All customer information from the original invoice that was posted in stage 1 is included.
    - Amounts are reported in the same **K_\*** elements as in the original invoice, but they have a positive sign.
    - The same markers that were applied in the original invoice are applied.
    - The **\<KorektaPodstawyOpodt\>** marker is applied.

    The base amount and tax amount from this invoice (internal document) are **not** included and reported in the **P_68** and **P_69** elements of the declaration part of the report.

> [!IMPORTANT]
> If stages 2 and 3 occur in the same reporting period, the **P_68** and **P_69** elements of the declaration part of the report aren't affected.

## Report RO and FP document types for retail operations

The JPK-V7 report in Finance supports reporting of the **RO** (Internal summary document) type (**\<TypDokumentu\>** tag under the **\<SprzedazWiersz\>** tag) 
for retail operations when the [Supplementary invoices for retail sales for Poland](emea-pol-vdek.md) feature is used.

### Business requirements

The following rules about reporting sales invoices for retail operations are based on the clarifications that are published in the Q&A section of the official tax portal of the Ministry of Finance of Poland:

- All fiscal receipts that are printed and given to the customers must be aggregated and reported as documents of the **RO** type (summarized invoice). Sales to non-domestic customers must be excluded from aggregation and reported as normal invoices (without a document type marker). Aggregation should be done for the reporting period. Sales documents that are reported as documents of the **RO** type (summarized invoice) aren't subject to **GTU** markers. Domestic sales that are aggregated for reporting as taxable documents of the **RO** type must also be reported as separate taxable documents of the **FP** type if the customer requested an invoice for those sales. Invoices that are marked as documents of the **FP** type must be excluded from totals in both **SprzedazCtrl** and all related **P_\*** values of the declaration part. Sales documents that are reported as documents of the **FP** type are subject to **GTU** markers.

### Initial assumptions for the reporting of fiscal documents in a JPK-V7

- All the documents that come from the point of sale (POS) are fiscalized.
- Information about fiscal receipts that are processed at the POS is correctly reflected in the following system database tables:

    - RetailTransactionTable
    - RetailTransactionSalesTrans
    - RetailTransactionTaxTrans

- If a customer provided a VAT number for the fiscal receipt at the POS, it's stored in the RetailTransactionFiscalCustomer.SerializedData table.
- All the fiscal receipts and pre-aggregated fiscal documents that were posted via a retail statement, and that must be aggregated for reporting purposes, are posted with a status of **Fiscal document** or **Fiscal document converted to invoice** in the Customer invoice journal.
- If an invoice was created at the POS, it's correctly reflected in the RetailTransactionSupplementaryInvoice table.
- If a fiscal receipt was converted from a fiscal document to an invoice, it has an invoice status of **Fiscal document converted to invoice** in the Customer invoice journal. (This assumption applies only to fiscal documents that aren't pre-aggregated.)
- Only posted retail transactions of the **Sales** type are considered retail invoices for the purpose of reporting as documents of the **FP** type.
- Specific scenarios, such as the "Gift card" scenario, are currently out of scope.

### Supported business user scenario in Finance

To report the **RO** and **FP** document types for retail operations, use the following parameters in the **Retail-specific sales marking** group of parameters of the **Wygenerowanie JPK_V7M** (if your company reports JPK-V7 monthly) or **Wygenerowanie JPK-V7K** (if your company reports JPK-V7 quarterly) that runs the **EMGenerateJPKVDEKReportController_PL** executable class (**Tax** \> **Setup** \> **Electronic messaging** \> **Executable class settings**):

- The **Aggregate fiscal documents** checkbox activates **Criteria to collect customer invoices for aggregation (RO – summarized invoices)** records that are included to collect and aggregate fiscal receipts that must be reported as documents of the **RO** type.
- The **Report retail POS invoices** checkbox collects retail invoices that have an invoice date in the reporting period and reports them as documents of the **FP** type.
- The **Report fiscal document converted to invoice** checkbox collects invoices from the CustInvoiceJour table that have a status of **Fiscal document converted to invoice** and **FiscalDocDate_PL** in the reporting period, and reports them as documents of the **FP** type.

#### Aggregate fiscal documents parameter

By default, the **Aggregate fiscal documents** checkbox is cleared. In this case, the system doesn't aggregate any documents. The documents are reported as standard documents where no document type is applied. Therefore, the report works as it worked before this change.

When the **Aggregate fiscal documents** checkbox is selected, domestic invoices that have a status of **Fiscal document** or **Fiscal document converted to invoice**, and that have a **Date of VAT register** value that falls in the reporting period, are reported as one aggregated document of the **RO** type for the reporting period. You define company-specific criteria of domestic fiscal documents that must be aggregated by using **Criteria to collect customer invoices for aggregation ("RO" - summarized invoices)** records.

When the aggregated **RO** document is included in the report, it has the following header fields.

| Reporting tag      | Value                                 |
|--------------------|---------------------------------------|
| KodKrajuNadaniaTIN | PL                                    |
| NrKontrahenta      | BRAK                                  |
| NazwaKontrahenta   | Sprzedaz paragonowa                   |
| DowodSprzedazy     | ROyyyyMMdd                            |
| DataWystawienia    | The last date of the reporting period |
| DataSprzedazy      | The last date of the reporting period |
| TypDokumentu       | RO                                    |

#### Report retail POS invoices parameter

By default, the **Report retail POS invoices** checkbox is cleared. When it's selected, the system collects retail invoices that meet the following criteria:

- There must be a retail invoice in the RetailTransactionSupplementaryInvoice table for the retail transaction in the RetailTransactionTable table.
- **RetailTransactionTable.Type** must equal **RetailTransactionType::Sales**.
- **RetailTransactionTable.entryStatus** must equal **RetailEntryStatus::Posted**, and the **RetailTransactionTable.StatementId** field must not be blank.
- The invoice date (**RetailTransactionSupplementaryInvoice.InvoiceDate**) is in the reporting period.

The fields of retail POS invoices must be filled in as shown in the following table.

| Reporting tag      | Value                                                                                                               |
|--------------------|---------------------------------------------------------------------------------------------------------------------|
| KodKrajuNadaniaTIN | PL                                                                                                                  |
| NrKontrahenta      | "BRAK" or RetailTransactionFiscalCustomer.SerializedData                                                            |
| NazwaKontrahenta   | The name of the customer from the customer master data (RetailTransactionSupplementaryInvoice.AccountNum) or "BRAK" |
| DowodSprzedazy     | RetailTransactionSupplementaryInvoice.InvoiceId                                                                     |
| DataWystawienia    | RetailTransactionSupplementaryInvoice.InvoiceDate                                                                   |
| DataSprzedazy      | RetailTransactionSalesTrans.TransDate                                                                               |
| TypDokumentu       | FP                                                                                                                  |

The fields of the SAFTTaxTransByReportingCode_PL table are filled in from the following data sources.

| Table name                            | Field names                                                                                        |
|---------------------------------------|----------------------------------------------------------------------------------------------------|
| RetailTransactionTable                | Type, EntryStatus, StatementId, Channel, Store, Terminal, TransactionId                            |
| RetailTransactionTaxTrans             | TaxCode, TaxPercentage, TaxBaseAmount, Amount, IsExempt, Channel, StoreId, Terminal, TransactionId |
| RetailTransactionSupplementaryInvoice | InvoiceId, InvoiceDate, AccountNum, CustInvoiceJour, Channel, Store, Terminal, TransactionId       |
| RetailTransactionSalesTrans           | TaxGroup, TaxItemGroup, TransDate, Currency, Channel, Store, TerminalId, TransactionId             |
| RetailTransactionFiscalCustomer       | SerializedData, Channel, Store, Terminal, TransactionId                                            |

#### Report fiscal document converted to invoice parameter

By default, the **Report fiscal document converted to invoice** checkbox is cleared. In this case, if the set of tax transactions and related customer invoices were aggregated and reported as documents of the **RO** type, they are excluded from the set of transactions that are reported in the standard.

When the **Report fiscal document converted to invoice** checkbox is selected, the system collects invoices from the CustInvoiceJour table by using the same **Criteria to collect customer invoices for aggregation** records that are defined for domestic invoices for aggregation. However, the following additional criteria are also used:

- **CustInvoiceJour_PL.FiscalDocState_PL** must equal **Fiscal document converted to invoice**.
- **CustInvoiceJour_PL.FiscalDocDate_PL** must be in the reporting period.

During preprocessing, these invoices are treated as standard invoices. The only difference is that their document type is set to **FP**.

## Report invoices from counterparties in different countries or regions that have identical NIP numbers 

The data structure in the JPK_V7 report collects the first International Organization for Standardization (ISO) country/region code that is found from the Tax exempt numbers table and posted in the Tax transactions table. Use different tax-exempt numbers for counterparties from different countries or regions. To differentiate identical tax-exempt numbers from different countries or regions during setup, use a prefix that includes an ISO country/region code. The first two letters of the ISO country/region code will be omitted during reporting in the **NrDostawcy** tag.

## Split payment (MPP) marker

The JPK-V7 report supports reporting of the **MPP** marker for both sales registers and purchase registers for reporting periods before July 1, 2021. The **MPP** marker isn't required for periods after July 1, 2021.

If a company performs operations that a split payment procedure must be applied to, the **Split payment** feature must be used.

When the **Split payment** feature is used, you don't have to complete any specific setup to report the **MPP** marker in a JPK-V7. The following algorithm is used to identify the **MPP** marker:

- The system provides a check of the **Split payment** and **Voluntary split payment** parameters of the customer transaction that is related to a sales invoice. If the **Split payment** parameter is selected, and the **Voluntary split payment** parameter is cleared, the related invoice will be reported with the **MPP** marker.
- The system provides a check of the **Split payment** and **Voluntary split payment** parameters of the vendor transaction that is related to a vendor invoice. If the **Split payment** parameter is selected, and the **Voluntary split payment** parameter is cleared, the related invoice will be reported with the **MPP** marker.
