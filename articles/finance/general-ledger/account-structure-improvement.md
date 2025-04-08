---
title: Account structure activation performance enhancement
description: Learn about the new performance enhancement for the account structure activation process, including an outline on account structure activation tips.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: conceptual
ms.date: 10/31/2022
ms.custom:
ms.reviewer: kfend
audience: Application User 
ms.search.region: Global 
ms.search.validFrom: 2022-10-08
ms.search.form:
ms.dyn365.ops.version: 10.0.31
---

# Account structure activation performance enhancement

[!include [banner](../includes/banner.md)]

This performance enhancement lets you activate account structures more quickly by running multiple transaction updates at the same time. In addition, the structure itself is marked as active after it's validated, and transaction processing can continue while existing unposted transactions are updated to the new structure. Because transactions updates might take some time, you can track the status of your activation by selecting **View activation status** above the grid on the **Account structures** page. You can also view your activation status by selecting **View** on the Action Pane and then selecting **Activation status** on the drop-down menu.

[![Account structures page.](./media/AccountStructure1.png)](./media/AccountStructure1.png)

After you select **View activation status**, a dialog box appears that shows the individual tasks that are running as part of the activation process. For each task, you can view the status and, after the task is completed, the completion date and time.

[![Account structure activation timeline.](./media/AccountStructureTimeline.png)](./media/AccountStructureTimeline.png)

## Account structure activation tips

The account structure activation dialog box that appears when you select **Activate** for a draft account structure has a tab section that is named **Update unposted transactions**. This section includes an option that is named **Force update**. You can select this option to update all unposted transactions to the current structure. However, you should use this option only when an error has occurred or Microsoft Support has directed you to use it.

Here are some of the factors that can affect the performance of the activation process:

- A large number of unposted journal records
- A large number of open source document records such as free text invoices, vendor invoices, and related documents that use the source document framework and have open accounting distributions
- The amount of data in TaxUncommitted
- The amount of open budget data
- Import of journal data while activation tasks are still running

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
