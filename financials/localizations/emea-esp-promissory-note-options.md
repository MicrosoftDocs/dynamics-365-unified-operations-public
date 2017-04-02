---
# required metadata

title: Spanish promissory note options
description: This topic describes options and changes for the basic promissory note functionality that is implemented in Microsoft Dynamics 365 for Operations for legal entities in Spain.
author: ShylaThompson
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264624
ms.assetid: a4925301-e193-49ce-814d-a0b71899118d
ms.search.region: Spain
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

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

