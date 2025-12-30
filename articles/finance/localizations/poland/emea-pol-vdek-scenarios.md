---
title: Details of specific business scenarios in the JPK-V7 report
description: Learn about details of specific business scenarios in the JPK-V7 report in Poland, including an outline on reporting overdue customer invoices.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 12/30/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Poland
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
---

# Details of specific business scenarios in the JPK-V7 report

[!include [banner](../../includes/banner.md)]

This article explains details of specific business scenarios in the JPK-V7 report in Poland.

## Reporting of overdue customer invoices

JPK-V7 report in Microsoft Dynamics 365 Finance supports reporting of overdue customer invoices when the local Polish [Overdue debt VAT](emea-pol-sales-tax-reports.md#allowance-for-bad-debts) feature is used.

### Business requirement

- If the company applies the procedure, the **\<P_68\>** element of the declaration part must report the amount of the taxable base for overdue invoices in the reporting period (that is, transactions that are posted to deduct value-added tax (VAT) for issued invoices that aren't paid within 150 days after the payment due date).
- If the company applies the procedure, the **\<P_69\>** element of the declaration part must report the amount of VAT for overdue invoices in the reporting period (that is, transactions that are posted to deduct VAT for issued invoices that aren't paid within 150 days after the payment due date).
- If the company applies the procedure, for overdue invoices in the period where the due date is 150 days, this transaction must be reported. Information about the customer from the original invoice and an amount that has a minus sign (–) must be included.
- If the company applies the procedure, for paid overdue invoices in the period when an overdue invoice was paid, this transaction must be reported. All the information about the customer from the original invoice and an amount that has a plus sign (+) must be included.
- If the company applies the procedure, and if overdue and paid overdue transactions are in the same reporting period, you can optionally report both transactions together in the sales register. In this case, the **\<P_68\>** and **\<P_69\>** elements of the declaration part aren't reported.

### Supported business user scenario in Finance

When a customer invoice is overdue, the invoice that you send to the customer goes through three stages:

1. You send the invoice to the customer. The system posts tax transactions. The invoice appears in **JPK** > **Ewidencja** > **SprzedazWiersz** as usual, according to the tax setup and marker setup.
1. If the customer doesn't pay the invoice within 150 days after the payment due date, the company can apply the [Overdue debt VAT](emea-pol-sales-tax-reports.md#allowance-for-bad-debts) periodic task by going to **Accounts receivable** > **Periodic tasks** > **Overdue debt VAT**. Tax transactions that this task produces appear in the JPK-V7M report. The report includes the following information:

    - All the customer information from the original invoice that you posted in stage 1.
    - Amounts are reported in the same **K_\*** elements as in the original invoice, but they have a negative sign.
    - The same markers that you applied in the original invoice.
    - The **\<KorektaPodstawyOpodt\>** marker.

    Moreover, the base amount and tax amount from this invoice (internal document) are included and reported in the **P_68** and **P_69** elements of the declaration part of the report.

1. If the customer pays the invoice after both stage 1 and stage 2 occur, the company must again apply the **Overdue debt VAT** periodic task in the period when the invoice was paid. The resulting tax transactions appear in the JPK-V7 report. The report includes the following information:

    - All customer information from the original invoice that you posted in stage 1.
    - Amounts are reported in the same **K_\*** elements as in the original invoice, but they have a positive sign.
    - The same markers that you applied in the original invoice.
    - The **\<KorektaPodstawyOpodt\>** marker.

    The base amount and tax amount from this invoice (internal document) are **not** included and reported in the **P_68** and **P_69** elements of the declaration part of the report.

> [!IMPORTANT]
> If stages 2 and 3 occur in the same reporting period, the **P_68** and **P_69** elements of the declaration part of the report aren't affected.

## Report RO and FP document types for retail operations

The JPK-V7 report in Finance supports reporting of the **RO** (Internal summary document) type (**\<TypDokumentu\>** tag under the **\<SprzedazWiersz\>** tag) 
for retail operations when you use the [Supplementary invoices for retail sales for Poland](emea-pol-vdek.md) feature.

### Business requirements

The following rules about reporting sales invoices for retail operations are based on the clarifications that are published in the Q&A section of the official tax portal of the Ministry of Finance of Poland:

- You must aggregate and report all fiscal receipts that you print and give to the customers as documents of the **RO** type (summarized invoice). You must exclude sales to nondomestic customers from aggregation and report them as normal invoices (without a document type marker). You should aggregate sales for the reporting period. Sales documents that you report as documents of the **RO** type (summarized invoice) aren't subject to **GTU** markers. You must also report domestic sales that you aggregate for reporting as taxable documents of the **RO** type as separate taxable documents of the **FP** type if the customer requested an invoice for those sales. You must exclude invoices that you mark as documents of the **FP** type from totals in both **SprzedazCtrl** and all related **P_\*** values of the declaration part. Sales documents that you report as documents of the **FP** type are subject to **GTU** markers.

### Initial assumptions for the reporting of fiscal documents in a JPK-V7

- All the documents that come from the point of sale (POS) are fiscalized.
- Information about fiscal receipts that the POS processes is correctly reflected in the following system database tables:

    - RetailTransactionTable
    - RetailTransactionSalesTrans
    - RetailTransactionTaxTrans

- If a customer provides a VAT number for the fiscal receipt at the POS, it's stored in the RetailTransactionFiscalCustomer.SerializedData table.
- You post all the fiscal receipts and preaggregated fiscal documents that a retail statement posts and that you must aggregate for reporting purposes with a status of **Fiscal document** or **Fiscal document converted to invoice** in the Customer invoice journal.
- If you create an invoice at the POS, it's correctly reflected in the RetailTransactionSupplementaryInvoice table.
- If you convert a fiscal receipt from a fiscal document to an invoice, it has an invoice status of **Fiscal document converted to invoice** in the Customer invoice journal. (This assumption applies only to fiscal documents that aren't preaggregated.)
- You consider only posted retail transactions of the **Sales** type as retail invoices for the purpose of reporting as documents of the **FP** type.
- Specific scenarios, such as the "Gift card" scenario, are currently out of scope.

### Supported business user scenario in Finance

To report the **RO** and **FP** document types for retail operations, use the following parameters in the **Retail-specific sales marking** group of parameters of the **Wygenerowanie JPK_V7M** (if your company reports JPK-V7 monthly) or **Wygenerowanie JPK-V7K** (if your company reports JPK-V7 quarterly) that runs the **EMGenerateJPKVDEKReportController_PL** executable class (**Tax** \> **Setup** \> **Electronic messaging** \> **Executable class settings**):

- Select the **Aggregate fiscal documents** checkbox to activate the **Criteria to collect customer invoices for aggregation (RO – summarized invoices)** records. These criteria include rules to collect and aggregate fiscal receipts that you must report as documents of the **RO** type.
- Select the **Report retail POS invoices** checkbox to collect retail invoices that have an invoice date in the reporting period and report them as documents of the **FP** type.
- Select the **Report fiscal document converted to invoice** checkbox to collect invoices from the CustInvoiceJour table that have a status of **Fiscal document converted to invoice** and **FiscalDocDate_PL** in the reporting period, and report them as documents of the **FP** type.

#### Aggregate fiscal documents parameter

By default, the **Aggregate fiscal documents** checkbox is cleared. In this case, the system doesn't aggregate any documents. The documents are reported as standard documents where no document type is applied. Therefore, the report works as it worked before this change.

When you select the **Aggregate fiscal documents** checkbox, domestic invoices that have a status of **Fiscal document** or **Fiscal document converted to invoice**, and that have a **Date of VAT register** value that falls in the reporting period, are reported as one aggregated document of the **RO** type for the reporting period. You define company-specific criteria of domestic fiscal documents that must be aggregated by using **Criteria to collect customer invoices for aggregation ("RO" - summarized invoices)** records.

When you include the aggregated **RO** document in the report, it has the following header fields.

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

By default, the **Report retail POS invoices** checkbox is cleared. When you select it, the system collects retail invoices that meet the following criteria:

- There must be a retail invoice in the RetailTransactionSupplementaryInvoice table for the retail transaction in the RetailTransactionTable table.
- **RetailTransactionTable.Type** must equal **RetailTransactionType::Sales**.
- **RetailTransactionTable.entryStatus** must equal **RetailEntryStatus::Posted**, and the **RetailTransactionTable.StatementId** field must not be blank.
- The invoice date (**RetailTransactionSupplementaryInvoice.InvoiceDate**) is in the reporting period.

You must fill in the fields of retail POS invoices as shown in the following table.

| Reporting tag      | Value                                                                                                               |
|--------------------|---------------------------------------------------------------------------------------------------------------------|
| KodKrajuNadaniaTIN | PL                                                                                                                  |
| NrKontrahenta      | "BRAK" or RetailTransactionFiscalCustomer.SerializedData                                                            |
| NazwaKontrahenta   | The name of the customer from the customer master data (RetailTransactionSupplementaryInvoice.AccountNum) or "BRAK" |
| DowodSprzedazy     | RetailTransactionSupplementaryInvoice.InvoiceId                                                                     |
| DataWystawienia    | RetailTransactionSupplementaryInvoice.InvoiceDate                                                                   |
| DataSprzedazy      | RetailTransactionSalesTrans.TransDate                                                                               |
| TypDokumentu       | FP                                                                                                                  |

You fill in the fields of the SAFTTaxTransByReportingCode_PL table from the following data sources.

| Table name                            | Field names                                                                                        |
|---------------------------------------|----------------------------------------------------------------------------------------------------|
| RetailTransactionTable                | Type, EntryStatus, StatementId, Channel, Store, Terminal, TransactionId                            |
| RetailTransactionTaxTrans             | TaxCode, TaxPercentage, TaxBaseAmount, Amount, IsExempt, Channel, StoreId, Terminal, TransactionId |
| RetailTransactionSupplementaryInvoice | InvoiceId, InvoiceDate, AccountNum, CustInvoiceJour, Channel, Store, Terminal, TransactionId       |
| RetailTransactionSalesTrans           | TaxGroup, TaxItemGroup, TransDate, Currency, Channel, Store, TerminalId, TransactionId             |
| RetailTransactionFiscalCustomer       | SerializedData, Channel, Store, Terminal, TransactionId                                            |

#### Report fiscal document converted to invoice parameter

By default, the **Report fiscal document converted to invoice** checkbox is cleared. In this case, if the set of tax transactions and related customer invoices were aggregated and reported as documents of the **RO** type, the system excludes them from the set of transactions that are reported in the standard.

When you select the **Report fiscal document converted to invoice** checkbox, the system collects invoices from the CustInvoiceJour table by using the same **Criteria to collect customer invoices for aggregation** records that you define for domestic invoices for aggregation. However, the system also uses the following additional criteria:

- **CustInvoiceJour_PL.FiscalDocState_PL** must equal **Fiscal document converted to invoice**.
- **CustInvoiceJour_PL.FiscalDocDate_PL** must be in the reporting period.

During preprocessing, the system treats these invoices as standard invoices. The only difference is that their document type is set to **FP**.

## Report invoices from counterparties in different countries or regions that have identical NIP numbers 

The data structure in the JPK_V7 report collects the first International Organization for Standardization (ISO) country or region code that it finds from the Tax exempt numbers table and posts in the Tax transactions table. Use different tax-exempt numbers for counterparties from different countries or regions. To differentiate identical tax-exempt numbers from different countries or regions during setup, use a prefix that includes an ISO country or region code. The first two letters of the ISO country or region code are omitted during reporting in the **NrDostawcy** tag.

## Split payment (MPP) marker

The JPK-V7 report supports reporting of the **MPP** marker for both sales registers and purchase registers for reporting periods before July 1, 2021. The **MPP** marker isn't required for periods after July 1, 2021. In version 3 of JPK-V7 schema, the MPP marker isn't applicable. 

If a company performs operations that a split payment procedure must be applied to for reporting periods before July 1, 2021, the **Split payment** feature must be used.

When you use the **Split payment** feature, you don't have to complete any specific setup to report the **MPP** marker in a JPK-V7. The following algorithm is used to identify the **MPP** marker:

- The system checks the **Split payment** and **Voluntary split payment** parameters of the customer transaction that is related to a sales invoice. If the **Split payment** parameter is selected, and the **Voluntary split payment** parameter is cleared, the related invoice is reported with the **MPP** marker.
- The system checks the **Split payment** and **Voluntary split payment** parameters of the vendor transaction that is related to a vendor invoice. If the **Split payment** parameter is selected, and the **Voluntary split payment** parameter is cleared, the related invoice is reported with the **MPP** marker.

## <a id="nrksef"></a>NrKSeF, OFF, BFK, DI - new XML tags in JPK-V7(3) to classify VAT record source

As part of the schema version 3, effective from February 1, 2026, the following XML tags are introduced:

- `<NrKSeF>` : Identifier number of the invoice in the National e-Invoice System
- `<OFF>` - Marker of the invoice referred to in Article 106nf of the Act, which doesn't have an identifier number in the National e-Invoice System and isn't sent to the National e-Invoice System
- `<BFK>` - Marker of the Electronic invoice or invoice in paper form
- `<DI>` - Marker of the other document than an invoice issued via the National e-Invoice System

### Implementation details

The NrKSeF, OFF, BFK, and DI tags are mutually exclusive. Dynamics 365 Finance automatically assigns these tags to each JPK‑V7 VAT entry to indicate whether the record originates from the KSeF system, was issued outside KSeF, represents a standard business invoice, or reflects an internal VAT document. The implementation logic ensures compliance with JPK‑V7 Schema version 3 requirements.

Dynamics 365 Finance determines the mutually exclusive `NrKSeF, OFF, BFK, DI` XML tags for JPK‑V7 reporting based on the origin and business context of each VAT record. The evaluation uses data from the tax transactions table, which is the primary source for the JPK‑V7 report, and considers the existence and attributes of related invoices and e‑invoicing data.

For each VAT line, the system attempts to identify a related invoice and applies the first matching condition according to the priority rules defined in the following sections. Only one of these tags is populated per JPK‑V7 record.

#### Outgoing Transactions (SprzedazWiersz)

For sales VAT records, the system applies the following logic in priority order:

##### NrKSeF

If a KSeF (National e‑Invoice System) number exists for the related invoice, the system populates the tag: `<NrKSeF>XXXXX</NrKSeF>`.

##### OFF

If no KSeF number exists, but an e‑invoicing submission log with a failed status is present (for example, due to KSeF unavailability), the system marks the record as issued outside KSeF by populating: `<OFF>1</OFF>`.

##### BFK

If neither a KSeF number nor a failed e‑invoicing submission exists, but the VAT record is linked to a related sales invoice, the system classifies the transaction as a business invoice and populates: `<BFK>1</BFK>`.

##### DI

If none of the above conditions apply (for example, the VAT record isn't linked to any sales invoice), the system treats the entry as an internal VAT document and populates: `<DI>1</DI>`.

Priority order for outgoing transactions: NrKSeF → OFF → BFK → DI.

#### Incoming Transactions (ZakupWiersz)

For purchase VAT records, the system applies the following evaluation logic:

##### NrKSeF

If a KSeF number exists for the related vendor invoice, the system populates: `<NrKSeF>XXXXX</NrKSeF>`.

##### BFK

If no KSeF number exists, but the VAT record is linked to a vendor invoice, the system classifies it as a business invoice and populates:
`<BFK>1</BFK>`.

##### DI

If the VAT record isn't linked to any vendor invoice, the system treats it as an internal VAT document and populates:
`<DI>1</DI>`.

Priority order for incoming transactions: NrKSeF → BFK → DI.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
