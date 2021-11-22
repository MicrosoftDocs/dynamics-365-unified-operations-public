---
# required metadata

title: Create monthly journal entries in a batch
description: This topic explains how to create journal entries in a batch to help increase efficiency when monthly lease expenses are recorded.
author: moaamer
ms.date: 08/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Dialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Create monthly journal entries in a batch

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


This topic explains how to create journal entries in a batch to help increase efficiency when monthly lease expenses are recorded. Batch processing can be used to create journal entries from multiple schedules. These journal entries can include lease payments, liability amortization, right-of-use (ROU) asset amortization, and executory cost expenses. You can also use batch processing to do the initial recognition of multiple leases at the same time, or to create transition adjustments for multiple leases at the same time.

To set up a batch job, or to process payment invoices, depreciation, or interest for multiple leases, go to **Asset leasing \> Periodic \> Batch journal creation**. In the dialog box that appears, you can select the schedule that the journal entries should be created from. You can also specify whether the batch process should be run for specific entities, lease groups, or lease books.

> [!NOTE]
> Subsequent transactions, such as liability amortization schedules, payments, depreciation, and expenses, will be posted only after the initial recognition for corresponding leases is posted.
>
> The journal entries are created, but they won't be posted until you select the **Run** command.

To post the initial recognition journal on a date other than the lease’s commencement date, select **Assigning initial recognition posting date**. A **Date** field will appear that lets you specify the correct posting date.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
