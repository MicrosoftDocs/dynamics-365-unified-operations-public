---
# required metadata

title: Fiscal archive for France
description: This topic describes the Fiscal archive and the Fiscal archive integrity verification tool that are available to Commerce customers in France
author: EvgenyPopovMBS
manager: annbe
ms.date: 07/20/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailGrandTotalJournalTable
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-2-19
ms.dyn365.ops.version: 10.0.17

---
# Fiscal archive for France

[!include [banner](../includes/banner.md)]

Fiscal archive is part of the [Cash register functionality for France](./emea-fra-cash-registers.md). A fiscal archive is an XML file that contains sales data for a store and a fiscal period. It includes the totals for the closed period, and also includes detailed data about sales transactions and events. The exported file is digitally signed, and the signature is contained in a separate file. It is required to keep exported fiscal archives on a secured external media for the legal retention period. It is also possible to verify the integrity of the fiscal archive and its data using the [Fiscal archive integrity verification tool](#fiscal-archive-integrity-verification-tool).

Fiscal archive can be exported from a closed period grand total journal. See [Period grand total journal](./emea-fra-cash-registers.md#period-grand-total-journal) for more information on how to work with period grand total journals.

The XML format of fiscal archive is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). See [Configure the archive export format](./emea-fra-cash-registers.md#configure-the-archive-export-format) to learn how to import and apply ER configurations that are required to export fiscal archive.

## Fiscal archive structure

A fiscal archive has the following structure:

  ``` xml
  <AchivePeriod> <!-- The identification of the period of the archive and the archive creation date -->
    <Company/> <!-- The identification of the company, including the SIRET code, the NAF code, and the VAT ID of the company -->
    <Store/> <!-- The identification of the store, including its address -->
    <PeriodGrandTotal/> <!-- The data of the period grand total journal that the archive was exported from -->
    <Shifts/> <!-- A collection of all shifts that were closed in the store during the period of the archive -->
      <Shift/> <!-- The data of a shift -->
    <Receipts/> <!-- A collection of all sales receipts that were registered in the shifts included in the archive -->
      <Receipt/> <!-- The data of a sales receipt -->
    <ReceiptCopies/> <!-- A collection of all sales receipt copies that were printed in the shifts included in the archive -->
      <ReceiptCopy> <!-- The data of a sales receipt copy  -->
    <AuditEvents> <!-- A collection of all signed audit events that were registered in the shifts included in the archive -->
      <AuditEvent/> <!-- The data of a signed audit event -->
  ```
### PeriodGrandTotal

The PeriodGrandTotal node of a fiscal archive contains the following elements:

| Element/Node                     | Comment |
|----------------------------------|---------|
| SequentialNumber                 | The sequential number of the signed period grand total journal for the store |
| FromDate                         | The starting date of the period of the journal |
| ToDate                           | The ending date of the period of the journal |
| TotalCashSales                   | The total amount of sales including tax for the period |
| TotalCashReturns                 | The absolute value of total amount of returns including tax for the period |
| GrandTotal                       | The total amount of sales including tax minus the absolute value of total amount of returns including tax for the period |
| PerpetualGrandTotal              | The cumulative perpetual grand total for the period, that is, the cumulative perpetual grand total for the previous period plus the total amount of sales including tax for the period minus the absolute value of total amount of returns including tax for the period |
| PerpetualGrandTotalAbsoluteValue | The cumulative perpetual grand total (absolute value) for the period, that is, the cumulative perpetual grand total (absolute value) for the previous period plus the total amount of sales including tax for the period plus the absolute value of total amount of returns including tax for the period |
| PeriodGrandTotalLines            | A collection of grand total amounts per tax rate |
| PeriodGrandTotalLine             | A node for the grand total amount for a tax rate |
| TotalInclTax                     | The grand total amount for the period for the tax rate|
| TaxRate                          | The tax rate|
| TaxAmount                        | The grand total amount of tax for the tax rate |
| DataToSign                       | The string that was [built from the elements of the period grand total journal record](./emea-fra-cash-registers.md#period-grand-total-journal), and that was used for signing |
| DataToSignFormatVersion          | The internal version of the format of data used for signing |
| Signature                        | The digital signature of the period grand total journal record |
| HashAlgorithm                    | The hash algorithm that was used for hashing the date before signing |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing |

### Shift

The Shift node of a fiscal archive contains the following elements:

| Element/Node                     | Comment |
|----------------------------------|---------|
| RegisterNumber                   | The identification of the register that the shift was opened on |
| Date                             | The date of the shift |
| TotalCashSales                   | The total amount of sales including tax for the shift |
| TotalCashReturns                 | The absolute value of total amount of returns including tax for the shift |
| GrandTotal                       | The total amount of sales including tax minus the absolute value of total amount of returns including tax for the shift |
| PerpetualGrandTotal              | The cumulative perpetual grand total for the shift, that is, the cumulative perpetual grand total for the previous shift of the same register plus the total amount of sales including tax for the shift minus the absolute value of total amount of returns including tax for the shift |
| PerpetualGrandTotalAbsoluteValue | The cumulative perpetual grand total for the shift, that is, the cumulative perpetual grand total for the previous shift of the same register plus the total amount of sales including tax for the shift plus the absolute value of total amount of returns including tax for the shift |
| ShiftLines                       | A collection of grand total amounts per tax rate |
| ShiftLine                        | A node for the grand total amount for a tax rate |
| TotalInclTax                     | The grand total amount for the shift for the tax rate |
| TaxRate                          | The tax rate |
| TaxAmount                        | The grand total amount of tax for the tax rate |
| SequentialNumber                 | The sequential number of the signed shift for the register |
| DataToSign                       | The string that was [built from the elements of the shift record](./emea-fra-cash-registers.md#digital-signing-of-closed-shifts), and that was used for signing |
| DataToSignFormatVersion          | The internal version of the format of data used for signing |
| Signature                        | The digital signature of the shift record |
| HashAlgorithm                    | The hash algorithm that was used for hashing the date before signing |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing |

## Fiscal archive integrity verification tool
