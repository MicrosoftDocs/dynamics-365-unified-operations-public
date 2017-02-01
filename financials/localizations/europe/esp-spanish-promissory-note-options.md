---
# required metadata

title: Spanish promissory note options | Microsoft Docs
description: This topic describes options and changes for the basic promissory note functionality that is implemented in Microsoft Dynamics 365 for Operations for legal entities in Spain.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-19 17:52:41
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 264624
ms.assetid: 57bd5860-5bce-44f2-962f-00b8ab54a9ce
ms.region: Spain
# ms.industry: 
ms.author: v-elgolu

---

# Spanish promissory note options

This topic describes options and changes for the basic promissory note functionality that is implemented in Microsoft Dynamics 365 for Operations for legal entities in Spain.

For legal entities in Spain, the promissory note functionality has additional options:

-   Validation for promissory notes journals
-   Dates in promissory notes journals
-   Invoice confirmation

## Accounts payable parameters for Spanish promissory notes
To set up parameters for promissory notes for legal entities in Spain, go to **Accounts payable parameters** &gt; **Promissory notes ES**.

## Validation for promissory notes journals
If the **Validation on promissory notes journal** parameter is set to **Yes**, the vendor's tax exempt number is validated when lines are added and fulfilled in a Promissory note settlement journal. If this parameter is set to **No**, and if **Domestic + EU member states** is selected in the **Tax exempt number requirement** field, the tax exempt number isn't validated.

## Dates in promissory notes journals
If the **Date treatment (promissory notes journal)** parameter is set to **Yes**, the **Minimum date** field is cleared when you create payment proposals for Draw promissory note journals and Remittance journals. Therefore, the due date is used as the transaction date, even if the due date is before the system date. If the **Date treatment (promissory notes journal)** parameter is set to **No**, the system date is the default date in the **Minimum date** field.

## Invoice confirmation
If the **Confirming invoices treatment** parameter is set to **Yes**, a separate line is created for each invoice number when you create payment proposals for Remittance journals and Settle promissory note journals. Separate lines are created, regardless of the selection in the **Period** field for the method of payment. Each invoice amount can be verified in the Remittance journal. If the **Confirming invoices treatment** parameter is set to **No**, journal lines can include amounts for multiple invoices, depending on the selection in the **Period** field.

