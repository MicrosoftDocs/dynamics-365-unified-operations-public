---
# required metadata

title: Configure an automated task for vendor invoice workflow
description: You can add an automated posting task to the Vendor invoice workflow so that the invoice is posted using a batch. 
author: abruer
manager: AnnBe
ms.date: 02/12/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14312
ms.assetid: 585d5b0b-1b79-4a03-ab18-528918070377
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2020-02-12
ms.dyn365.ops.version: AX 10.0.10

---
# Configure an automated task for vendor invoice workflow

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to add an automated posting task to the Vendor invoice workflow so that invoices are processed in a batch. Posting invoices in a batch lets the workflow process continue without having to wait for the posting to finish, which improves the overall performance of all the tasks submitted to the workflow.

The **Post the vendor invoice using a batch** task must not be used in the same workflow as the **Post vendor invoices** automated task. Also, the **Post the vendor invoice using a batch** task should be the last element in the workflow configuration.

To post a vendor invoice in a batch, on the **Feature management** page, turn on the **Add an automated task to the Vendor invoice workflow for posting the vendor invoice using a batch job** parameter. Vendor invoice workflows are configured by going to **Accounts payable > Setup > Accounts payable workflows**. 

