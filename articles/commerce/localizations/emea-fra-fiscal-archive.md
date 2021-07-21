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

The XML format of fiscal archive is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). See [Configure the archive export format](./emea-fra-cash-registers.md#configure-the-archive-export-format) to learn how to import and apply ER configurations that are required to export fiscal archives.

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
| HashAlgorithm                    | The hash algorithm that was used for hashing the data before signing |
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
| HashAlgorithm                    | The hash algorithm that was used for hashing the data before signing |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing |

### Receipt

The Receipt node of a fiscal archive contains the following elements:

| Element/Node                     | Comment |
|----------------------------------|---------|
| AppVersion                       | The identification of the version of the cash register software that was used to issue the receipt |
| Date                             | The date and time of the receipt in the format YYYYMMDDHHMMSS |
| NumberOfCopies                   | The number of times a copy was printed for the receipt |
| OperatorCode                     | The code of the operator that issued the receipt |
| OperatorName                     | The name of the operator that issued the receipt |
| RegisterNumber                   | The identification of the register that the receipt was issued from |
| CustomerAccount                  | The identification of the customer that the receipt was issued for |
| LineCount                        | The number of sales lines in the receipt |
| Total                            | The Total node of the receipt |
| ExclTax                          | The total amount of the receipt excluding tax |
| InclTax                          | The total amount of the receipt including tax |
| PaymentLines                     | A collection of payment lines of the receipt |
| PaymentLine                      | A node for a payment |
| Type                             | The identification of the payment type as configured in the cash register |
| Name                             | The name of the payment type as configured in the cash register |
| Amount                           | The amount of payment in the store's currency |
| AmountCur                        | The amount of payment in the payment currency |
| Currency                         | The identification of the payment currency |
| CurrencyRate                     | The currency rate multiplied by 100 and rounded to a whole number |
| ReceiptLines                     | A collection of receipt lines |
| ReceiptLine                      | A node for a receipt line |
| Product                          | The identification of the product on the receipt line |
| Name                             | The name of the product on the receipt line |
| TaxRates                         | A collection of tax lines linked to the receipt line |
| LineTaxRate                      | A node for a tax line |
| TaxRate                          | The tax rate of the tax line |
| TaxAmount                        | The amount of tax of the tax line |
| Quantity                         | The quatity of the product sold |
| UnitId                           | The identification of the unit of the product sold |
| UnitPriceExclTax                 | The unit price of the product excluding taxes |
| UnitPriceInclTax                 | The unit price of the product including taxes |
| TotalExclTax                     | The total amount of the receipt line excluding tax |
| TotalInclTax                     | The total amount of the receipt line including tax |
| Discounts                        | A collection of discounts applied to the receipt line |
| FooterLines                      | A collection of receipt total amounts per tax rate |
| FooterLine                       | A node for a receipt total amount for a tax rate |
| TotalExclTax                     | The total amount of the receipt excluding taxes for the tax rate |
| TotalInclTax                     | The total amount of the receipt including taxes for the tax rate |
| TaxRate                          | The tax rate |
| TaxAmount                        | The  total amount of tax for the tax rate |
| SequentialNumber                 | The sequential number of the signed sales transaction for the register |
| DataToSign                       | The string that was [built from the elements of the sales transaction record](./emea-fra-cash-registers.md#digital-signing-of-sales-transactions), and that was used for signing |
| DataToSignFormatVersion          | The internal version of the format of data used for signing |
| Signature                        | The digital signature of the sales transaction record |
| HashAlgorithm                    | The hash algorithm that was used for hashing the data before signing |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing |

### ReceiptCopy

The ReceiptCopy node of a fiscal archive contains the following elements:

| Element/Node                    | Comment |
|---------------------------------|---------|
| RegisterNumber                  | The register number that the copy of receipt is printed from |
| CopyNumber                      | The number of the receipt copy for this sales transaction |
| SequentialNumber                | The sequential number of the signed receipt copy event for this register |
| OriginalReceiptNumber           | The printed receipt number of the original sales transaction|
| OriginalReceiptSequentialNumber | The sequential number of the original sales transaction |
| Date                            | The date and time of the receipt copy event in the format YYYYMMDDHHMMSS |
| OperatorCode                    | The code of the operator that issued the receipt |
| OperatorName                    | The name of the operator that issued the receipt |
| DataToSign                      | The string that was [built from the elements of the receipt copy record](./emea-fra-cash-registers.md#digital-signing-of-receipt-copies), and that was used for signing|
| DataToSignFormatVersion         | The internal version of the format of data used for signing |
| Signature                       | The digital signature of the receipt copy record |
| HashAlgorithm                   | The hash algorithm that was used for hashing the data before signing |
| CertificateThumbprint           | The thumbprint of the certificate that was used for signing |

## Fiscal archive integrity verification tool
