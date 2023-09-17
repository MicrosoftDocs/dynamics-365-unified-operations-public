---
title: Fiscal archive for France
description: This article provides information about the fiscal archive and the Fiscal archive integrity verification tool that are available in the Microsoft Dynamics 365 Commerce localization for France.
author: EvgenyPopovMBS
ms.date: 11/17/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: France
ms.author: josaw
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: 10.0.17
ms.search.industry: Retail
ms.search.form: RetailGrandTotalJournalTable
---
# Fiscal archive for France

[!include [banner](../includes/banner.md)]

This article provides information about the fiscal archive and the Fiscal archive integrity verification tool that are available in the Microsoft Dynamics 365 Commerce localization for France. The fiscal archive is part of the [cash register functionality for France](./emea-fra-cash-registers.md).

A fiscal archive is an XML file that contains sales data for a store and a fiscal period. It includes the totals for the closed period, and detailed data about sales transactions and events.

A fiscal archive can be exported from a closed period grand total journal. (For more information about how to work with period grand total journals, see [Period grand total journal](./emea-fra-cash-registers.md#period-grand-total-journal).) The exported fiscal archive XML file is digitally signed, and the digital signature is contained in a separate file. Exported fiscal archives must be kept on secured external media for the legal retention period.

You can verify the integrity of the fiscal archive and its data by using the [Fiscal archive integrity verification tool](#fiscal-archive-integrity-verification-tool).

The XML format of the fiscal archive is implemented by using [Electronic reporting (ER)](../../dev-itpro/analytics/general-electronic-reporting.md). For information about how to import and apply the ER configurations that are required to export fiscal archives, see [Configure the Z report and archive export formats](./emea-fra-cash-registers.md#configure-the-z-report-and-archive-export-formats).

## Fiscal archive structure

A fiscal archive has the following structure.

``` xml
<AchivePeriod> <!-- The identification of the period of the archive and the archive creation date. -->
    <Company/> <!-- The identification of the company, including the SIRET code, the NAF code, and the VAT ID of the company. -->
    <Store/> <!-- The identification of the store, including its address. -->
    <PeriodGrandTotal/> <!-- The data of the period grand total journal that the archive was exported from. -->
    <Shifts/> <!-- A collection of all shifts that were closed in the store during the period of the archive. -->
        <Shift/> <!-- The data of a shift. -->
    <Receipts/> <!-- A collection of all sales receipts that were registered in the shifts included in the archive. -->
        <Receipt/> <!-- The data of a sales receipt. -->
    <ReceiptCopies/> <!-- A collection of all sales receipt copies that were printed in the shifts included in the archive. -->
        <ReceiptCopy> <!-- The data of a sales receipt copy. -->
    <AuditEvents> <!-- A collection of all signed audit events that were registered in the shifts included in the archive. -->
        <AuditEvent/> <!-- The data of a signed audit event. -->
```

### PeriodGrandTotal node

The **PeriodGrandTotal** node of a fiscal archive contains the following elements.

| Element/Node                     | Comment |
|----------------------------------|---------|
| SequentialNumber                 | The sequential number of the signed period grand total journal for the store. |
| FromDate                         | The start date of the period of the journal. |
| ToDate                           | The end date of the period of the journal. |
| TotalCashSales                   | The total amount of sales, including tax, for the period. |
| TotalCashReturns                 | The absolute value of the total amount of returns, including tax, for the period. |
| GrandTotal                       | The total amount of sales, including tax, minus the absolute value of the total amount of returns, including tax, for the period. |
| PerpetualGrandTotal              | The cumulative perpetual grand total for the period. In other words, the cumulative perpetual grand total for the previous period, plus the total amount of sales, including tax, for the period, minus the absolute value of the total amount of returns, including tax, for the period. |
| PerpetualGrandTotalAbsoluteValue | The cumulative perpetual grand total (absolute value) for the period. In other words, the cumulative perpetual grand total (absolute value) for the previous period, plus the total amount of sales, including tax, for the period, plus the absolute value of the total amount of returns, including tax, for the period. |
| PeriodGrandTotalLines            | A collection of grand total amounts per tax rate. |
| PeriodGrandTotalLine             | A node for the grand total amount for a tax rate. |
| TotalInclTax                     | The grand total amount for the period for the tax rate. |
| TaxRate                          | The tax rate. |
| TaxAmount                        | The grand total amount of tax for the tax rate. |
| DataToSign                       | The string that was [built from the elements of the period grand total journal record](./emea-fra-cash-registers.md#period-grand-total-journal) and used for signing. |
| DataToSignFormatVersion          | The internal version of the format of data that was used for signing. |
| Signature                        | The digital signature of the period grand total journal record. |
| HashAlgorithm                    | The hash algorithm that was used to hash the data before signing. |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing. |

### Shift node

The **Shift** node of a fiscal archive contains the following elements.

| Element/Node                     | Comment |
|----------------------------------|---------|
| RegisterNumber                   | The identification of the register that the shift was opened on. |
| Date                             | The date of the shift. |
| TotalCashSales                   | The total amount of sales, including tax, for the shift. |
| TotalCashReturns                 | The absolute value of the total amount of returns, including tax, for the shift. |
| GrandTotal                       | The total amount of sales, including tax, minus the absolute value of the total amount of returns, including tax, for the shift. |
| PerpetualGrandTotal              | The cumulative perpetual grand total for the shift. In other words, the cumulative perpetual grand total for the previous shift of the same register, plus the total amount of sales, including tax, for the shift, minus the absolute value of the total amount of returns, including tax, for the shift. |
| PerpetualGrandTotalAbsoluteValue | The cumulative perpetual grand total for the shift. In other words, the cumulative perpetual grand total for the previous shift of the same register, plus the total amount of sales, including tax, for the shift, plus the absolute value of the total amount of returns, including tax, for the shift. |
| ShiftLines                       | A collection of grand total amounts per tax rate. |
| ShiftLine                        | A node for the grand total amount for a tax rate. |
| TotalInclTax                     | The grand total amount for the shift for the tax rate. |
| TaxRate                          | The tax rate. |
| TaxAmount                        | The grand total amount of tax for the tax rate. |
| SequentialNumber                 | The sequential number of the signed shift for the register. |
| DataToSign                       | The string that was [built from the elements of the shift record](./emea-fra-cash-registers.md#digital-signing-of-closed-shifts) and used for signing. |
| DataToSignFormatVersion          | The internal version of the format of data that was used for signing. |
| Signature                        | The digital signature of the shift record. |
| HashAlgorithm                    | The hash algorithm that was used to hash the data before signing. |
| CertificateThumbprint            | The thumbprint of the certificate that was used for signing. |

### Receipt node

The **Receipt** node of a fiscal archive contains the following elements.

| Element/Node            | Comment |
|-------------------------|---------|
| AppVersion              | The identification of the version of the cash register software that was used to issue the receipt. |
| Date                    | The date and time of the receipt in YYYYMMDDHHMMSS format. |
| NumberOfCopies          | The number of times that a copy was printed for the receipt. |
| OperatorCode            | The code of the operator who issued the receipt. |
| OperatorName            | The name of the operator who issued the receipt. |
| RegisterNumber          | The identification of the register that the receipt was issued from. |
| CustomerAccount         | The identification of the customer that the receipt was issued for. |
| LineCount               | The number of sales lines on the receipt. |
| Total                   | The total node of the receipt. |
| ExclTax                 | The total amount of the receipt, excluding tax. |
| InclTax                 | The total amount of the receipt, including tax. |
| PaymentLines            | A collection of payment lines of the receipt. |
| PaymentLine             | A node for a payment. |
| Type                    | The identification of the payment type, as configured in the cash register. |
| Name                    | The name of the payment type, as configured in the cash register. |
| Amount                  | The amount of payment in the store's currency. |
| AmountCur               | The amount of payment in the payment currency. |
| Currency                | The identification of the payment currency. |
| CurrencyRate            | The currency rate multiplied by 100 and rounded to a whole number. |
| ReceiptLines            | A collection of receipt lines. |
| ReceiptLine             | A node for a receipt line. |
| Product                 | The identification of the product on the receipt line. |
| Name                    | The name of the product on the receipt line. |
| TaxRates                | A collection of tax lines that are linked to the receipt line. |
| LineTaxRate             | A node for a tax line. |
| TaxRate                 | The tax rate of the tax line. |
| TaxAmount               | The amount of tax for the tax line. |
| Quantity                | The quantity of the product that was sold. |
| UnitId                  | The identification of the unit of the product that was sold. |
| UnitPriceExclTax        | The unit price of the product, excluding taxes. |
| UnitPriceInclTax        | The unit price of the product, including taxes. |
| TotalExclTax            | The total amount of the receipt line, excluding tax. |
| TotalInclTax            | The total amount of the receipt line, including tax. |
| Discounts               | A collection of discounts that are applied to the receipt line. |
| FooterLines             | A collection of receipt total amounts per tax rate. |
| FooterLine              | A node for a receipt total amount for a tax rate. |
| TotalExclTax            | The total amount of the receipt, excluding taxes for the tax rate. |
| TotalInclTax            | The total amount of the receipt, including taxes for the tax rate. |
| TaxRate                 | The tax rate. |
| TaxAmount               | The total amount of tax for the tax rate. |
| SequentialNumber        | The sequential number of the signed sales transaction for the register. |
| DataToSign              | The string that was [built from the elements of the sales transaction record](./emea-fra-cash-registers.md#digital-signing-of-sales-and-return-transactions) and used for signing. |
| DataToSignFormatVersion | The internal version of the format of data that was used for signing. |
| Signature               | The digital signature of the sales transaction record. |
| HashAlgorithm           | The hash algorithm that was used to hash the data before signing. |
| CertificateThumbprint   | The thumbprint of the certificate that was used for signing. |

### ReceiptCopy node

The **ReceiptCopy** node of a fiscal archive contains the following elements.

| Element/Node                    | Comment |
|---------------------------------|---------|
| RegisterNumber                  | The register number that the copy of the receipt was printed from. |
| CopyNumber                      | The number of the receipt copy for the sales transaction. |
| SequentialNumber                | The sequential number of the signed receipt copy event for the register. |
| OriginalReceiptNumber           | The printed receipt number of the original sales transaction.|
| OriginalReceiptSequentialNumber | The sequential number of the original sales transaction. |
| Date                            | The date and time of the receipt copy event in YYYYMMDDHHMMSS format. |
| OperatorCode                    | The code of the operator who printed the receipt copy. |
| OperatorName                    | The name of the operator who printed the receipt copy. |
| DataToSign                      | The string that was [built from the elements of the receipt copy record](./emea-fra-cash-registers.md#digital-signing-of-receipt-copies) and used for signing. |
| DataToSignFormatVersion         | The internal version of the format of data that was used for signing. |
| Signature                       | The digital signature of the receipt copy record. |
| HashAlgorithm                   | The hash algorithm that was used to hash the data before signing. |
| CertificateThumbprint           | The thumbprint of the certificate that was used for signing. |

### AuditEvent node

The **AuditEvent** node of a fiscal archive contains the following elements.

| Element/Node            | Comment |
|-------------------------|---------|
| Code                    | A predefined event code. |
| EventType               | A predefined event type. |
| Date                    | The date and time of the audit event in YYYYMMDDHHMMSS format. |
| RegisterNumber          | The register number that the audit event was registered in. |
| OperatorCode            | The code of the operator who registered the audit event. |
| OperatorName            | The name of the operator who registered the audit event. |
| SequentialNumber        | The sequential number of the signed audit event for the register. |
| DataToSign              | The string that was [built from the elements of the audit event record](./emea-fra-cash-registers.md#digital-signing-of-events) and used for signing. |
| DataToSignFormatVersion | The internal version of the format of data that was used for signing. |
| Signature               | The digital signature of the audit event record. |
| HashAlgorithm           | The hash algorithm that was used to hash the data before signing. |
| CertificateThumbprint   | The thumbprint of the certificate that was used for signing. |

## Fiscal archive integrity verification tool

The Fiscal archive integrity verification tool can be used to verify the integrity of a fiscal archive, and to detect violations of the signature of the archive and of the chains of signed records in the archive. The tool should be applied to a fiscal archive file and the corresponding signature file. When it's run, the tool performs the following actions:

1. Verify the signature of the fiscal archive file.
1. Verify signatures and signature chains of all fiscal archive records. (These records are the period grand total journal, shift, receipt, receipt copy, and audit event records.) For each record, the tool performs these actions:

    1. Build a text string from data elements of the record, according to the [digital signing rules](./emea-fra-cash-registers.md#digital-signing-overview) and the internal version of the format of data that was used to sign the record. These elements include the signature of the previous record of the same type.
    1. Calculate a hash code of the string by using the hash algorithm that was used to hash the data of the record before signing.
    1. Decrypt the signature of the record by using the public key of the digital certificate that was used to sign the record.
    1. Compare the result with the hash code that was calculated earlier.

1. Print all integrity violations that are found.

The Fiscal archive integrity verification tool takes the form of a Windows PowerShell script and is published via the Commerce software development kit (SDK).

To obtain the Fiscal archive integrity verification tool and run it against a fiscal archive, follow these steps.

1. Download the tool from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Open the last available release branch.
    1. Open **src \> FiscalIntegration \> SequentialSignatureFrance \> FiscalArchiveIntegrityVerificationTool**.
    1. Review the license terms for the tool.
    1. Download the contents of the folder to your local machine.

1. Export public key files for all digital certificates that are used for digital signing of transactions and audit events on the Commerce channel side, or period grand total journals and fiscal archives on the Commerce headquarters side.
1. Put the fiscal archive file, its signature file, and all public key files into one folder.
1. Run Windows PowerShell.
1. Run the **verify.ps1** script of the tool, and specify the name of the fiscal archive file. Include the full path of the file.
1. Review any integrity violations that are found.
