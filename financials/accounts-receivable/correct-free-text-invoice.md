---
# required metadata

title: Correct a free text invoice
description: This article explains how to correct a free text invoice that has been posted and reissue it as a corrected invoice.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustFreeInvoice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 13991
ms.assetid: 2a0a4789-8619-4974-bef9-0923cc848420
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Correct a free text invoice

[!include[banner](../includes/banner.md)]


This article explains how to correct a free text invoice that has been posted and reissue it as a corrected invoice.

To correct a free text invoice that has already been posted, open the posted free text invoice. On the **Invoice** page, select **Cancel**, and then select **Correct invoice**. Select a reason code, add comments, and select the date for new corrected invoice. You can modify the corrected invoice, and post it. 

When you post the corrected invoice, a canceling invoice is created for a credit amount that equals the original invoice amount. Therefore, the combined balance of the original invoice and the canceling invoice is 0 (zero). The canceling invoice is settled against the original invoice. 

After you post the corrected invoice, you will have three invoices:

-   **Original invoice** – The invoice that includes the information that you're correcting.
-   **Canceling invoice** – The system-generated credit invoice that was created to cancel the invoice that was most recently corrected.
-   **Corrected invoice** – The invoice that contains the corrected invoice information.

You can identify canceling and correcting invoices in two ways:

-   The **All free text invoices** page includes a **Correction** column, where you can see which invoices are canceling invoices and corrected invoices.
-   The header of the free text invoice shows a status of **Cancelling invoice '\[invoice number\]'** or **Corrected invoice '\[invoice number\]'**.

> [!NOTE]
> This feature is available only if the **Free text invoice correction** configuration key is selected.



