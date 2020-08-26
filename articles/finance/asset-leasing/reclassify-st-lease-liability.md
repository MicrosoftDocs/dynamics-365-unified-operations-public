---
# required metadata

title: Reclassify short term portion of lease liability
description: This topic describes the process for creating a monthly journal entry to reclassify a portion of the lease liability as short term.
author: moaamer
manager: Ann Beebe
ms.date: 08/06/2020
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
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: 10.0.14
---

# Reclassify short-term portion of lease liability

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process for creating a monthly journal entry to reclassify a portion of the lease liability as shor term. When the schedule that's selected in the batch process is **Short-term lease liability reclass**, a journal entry will be created. This entry is used to post current portion of the lease liability on the last day of the month. As the same time, reversal entry will be posted as of the first day of the next month.

The short-term portion of the lease liability is displayed on the liability amortization schedule. When the journal entry is posted, the **Liability reclass journal created** column will become enabled and the journal ID will also populate on the schedule.

1.	To create and post the short-term liability reclassification journal entry, open the Batch journal creation page (**Asset leasing > Periodic > Batch journal creation**).
2.	In the **Select schedule** dropdown, select **Short-term lease liability reclass**.
3.	In the **Lease group** dropdown, select a lease group or in the **Book ID dropdown**, select the **Book ID**.
4.	Enable the **Post parameter**, otherwise choose to disable for the entry to be created but not posted.
5.	Enable **Preview before posting** to view the entry before posting.
6.	Click **OK**.
