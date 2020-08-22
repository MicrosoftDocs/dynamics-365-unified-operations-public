---
# required metadata

title: Confirm payment schedules in batch
description:  This topic describes the process of creating journal entries in batch to increase efficiency when recording the monthly lease expense.
author: moaamer
manager: Ann Beebe
ms.date: 08/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: 10.0.14
---

# Create monthly journal entries in batch

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process of creating journal entries in batch to increase efficiency when recording the monthly lease expense. Batch processing can be used to create journal entries from multiple schedules. These journal entries can include lease payments, liability amortization, right-of-use asset amortization, and executory cost expenses. You can also use batch processing to initially recognize multiple leases at once, or to perform transition adjustments for multiple leases at once.

To setup a batch job or to process payment invoices, depreciation, or interest for multiple leases, open the **Batch journal creation** page (**Asset leasing > Periodic > Batch journal creation**).	A parameters dialog will appear where you can select the schedule that the journal entries will be created from, as well as whether to run the batch process for certain entities, lease groups, or individual lease books.
> [!Note]
> Subsequent transactions such as liability amortization schedule, payments, depreiation and expenses will be posted only after posting the initial recognition for respective leases.   



> [!Note]
> The journal entries are created but will not post until you click the **Run** command.
