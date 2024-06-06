---
title: Import customer payment with JBA file format
description: Learn how to import EFT files with a Japanese Bankers Association file format, including a step-by-step process using the JPMF demo data company.
author: kfend
ms.author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransCustPaym, SrsReportViewerForm
ms.dyn365.ops.version: Version 7.0.0
---

# Import customer payment with JBA file format

[!include [banner](../../includes/banner.md)]

In Japan, the Japanese Bankers Association (JBA) file format is commonly used for Electronic Fund Transfer (EFT) among banks. 



This task walks you through importing an EFT file with a JBA format.



This procedure was created using the demo company data JPMF.

1. Go to Accounts receivable > Payments > Payment journal.
2. Click New.
3. In the Name field, type 'CustPay'.
4. Click Lines.
5. Click Functions.
6. Click Import payments.
7. In the Method of payment field, type a value.
    * For example, enter the method of payment that uses JBA(JP) - Format A.  
8. Click OK.
    * Select the file to upload.  
9. Click OK.
10. Close the report
    * A control report is generated.  
    * Note that the payment amount and description are imported.  
11. In the Account field, specify the values 'JPMF-000001'.
12. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
