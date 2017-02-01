---
# required metadata

title: Spanish bill of exchange options | Microsoft Docs
description: This topic describes specific options and changes in basic bill of exchange process implemented in Microsoft Dynamics 365 for Operations for legal entities in Spain.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-19 18:00:38
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
ms.custom: 264644
ms.assetid: d28c4650-d91f-4349-8233-7c547dc28a6e
ms.region: Spain
# ms.industry: 
ms.author: v-elgolu

---

# Spanish bill of exchange options

This topic describes specific options and changes in basic bill of exchange process implemented in Microsoft Dynamics 365 for Operations for legal entities in Spain.

For legal entities in Spain, the bill of exchange functionality has additional options:

-   Validation for bill of exchange journals
-   Dates in bill of exchange journals

## Accounts receivable parameters for Spanish bills of exchange
To set up the parameters for bills of exchange for legal entities in Spain, go to **Accounts receivable parameters** &gt; **Bill of exchange ES**.

## Validation for bill of exchange journals
If the **Validation on bill of exchange journal** parameter is set to **Yes**, a bill of exchange isn't posted when transactions have the same voucher number and different transaction dates. This parameter applies to ledger journal transactions. This parameter is used only when the journal allows one voucher number, and when the **Validation on bill of exchange journals** option is selected on the **Accounts receivable parameters** page. The **Validation on bill of exchange journal** parameter affects the following documents:

-   Draw bill of exchange journal
-   Remittance journal
-   Protest bill of exchange journal
-   Redraw bill of exchange journal
-   Settle bill of exchange journal
-   Payment journal

## Dates in bill of exchange journals
If the **Date treatment on bill of exchange journal** parameter is set to **Yes**, the transaction date on bill of exchange journals is updated to the due date when a payment proposal is used. The **Date treatment on bill of exchange journal** parameter affects the following documents:

-   Remittance journal
-   Protest bill of exchange journal
-   Redraw bill of exchange journal


