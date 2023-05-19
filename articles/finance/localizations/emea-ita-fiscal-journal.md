---
title: Fiscal journal report
description: This article provides information about Fiscal journal report in Italy
author: liza-golub
ms.date: 05/19/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Italy
ms.author: liza-golub
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
---

# Fiscal journal report

The Italian **Fiscal journal** report (**General ledger \> Inquiries and reports \> Fiscal journal**) is a monthly report that lists all the vouchers and journal entries in order, by posting date.

This report includes the following fields:

-   Line number
-   Posting date
-   Competence date
-   Document number (voucher number)
-   Date for document
-   Ledger account number and name
-   Customer/Vendor account number and name
-   Description
-   Currency
-   Debit or credit amount of the document

![Fiscal journal report transactions.](media/ITA-Competence-date-for-transactions-1-fiscal-journal.png)

> [!NOTE]
> Use of the [One voucher](../general-ledger/one-voucher.md) functionality introduces a limitation on further Fiscal journal reporting for some scenarios that are subject to this report. Specifically, a bank statement scenario must be posted by using different vouchers for transactions that have different counteragent accounts. We recommend that you set the **Allow multiple transactions within one voucher** parameter on the **General ledger parameters** page to **No** in your legal entity if you post transactions that are part of the Fiscal journal report. For information about One voucher functionality, see [One voucher](../general-ledger/one-voucher.md).


## Fiscal journal page numbering improvements

You can enable the feature **(Italy) Fiscal journal page numbering improvements** in the **Feature management** workspace.

This feature improves the calculation logic for page numbering in the Italian fiscal journal report. To update and store the page numbers, print the report to a screen with the **Report PDF Viewer** feature enabled, or print the report to a file in PDF format. Page numbers are calculated using the new algorithm when the fiscal journal report is printed in PDF format. Page numbers are stored so that pages for the next month’s report start sequentially using the next number after the stored one. This feature also enables an algorithm for grouping lines with the same column values into one line, so that only the necessary pages are included in the report printout.

If you need to calculate the number of the documents included in the Fiscal journal, complete the following steps.

1.	Print the report in a PDF file format.
2.	Convert the PDF to Microsoft Excel using a converter software.
3.	Create a pivot table and in the **Rows** field, select **Docum. No.**.

    ![Excel pivot table.](media/ExcelPivotTable.png)

The number of documents is equal to number of lines in the pivot table.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

