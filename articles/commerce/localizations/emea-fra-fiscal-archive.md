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
    <Shifts/> <!-- The list of all shifts that were closed in the store during the period of the archive -->
      <Shift/> <!-- The data of a shift -->
    <Receipts/> <!-- The list of all sales receipts that were registered in the shifts included in the archive -->
      <Receipt/> <!-- The data of a sales receipt -->
    <ReceiptCopies/> <!-- The list of all sales receipt copies that were printed in the shifts included in the archive -->
      <ReceiptCopy> <!-- The data of a sales receipt copy  -->
    <AuditEvents> <!-- The list of all signed audit events that were registered in the shifts included in the archive -->
      <AuditEvent/> <!-- The data of a signed audit event -->
  ```
### PeriodGrandTotal

The PeriodGrandTotal node of a fiscal archive contains the following elements:

| Element/Node | Comment|
| SequentialNumber | |
| Date | |
| FromDate | |
| ToDate | |
| TotalCashSales | |
| TotalCashReturns | |
| GrandTotal | |
| PerpetualGrandTotal | |
| PerpetualGrandTotalAbsoluteValue | |
| PeriodGrandTotalLines | |
| PeriodGrandTotalLine | |
| TotalInclTax | |
| TaxRate | |
| TaxAmount | |
| DataToSign | |
| DataToSignFormatVersion | |
| Signature | |
| HashAlgorithm | |
| CertificateThumbprint | |

## Fiscal archive integrity verification tool
