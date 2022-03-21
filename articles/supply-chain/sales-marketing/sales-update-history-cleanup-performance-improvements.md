---
title: Clean up sales history data
description: This topic describes how to improve your system performance by scheduling the Sales update history cleanup periodic task to run at a regular interval
author: myvakalo
ms.date: 03/21/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-09-29
ms.dyn365.ops.version: 10.0.19
---

# Clean up sales history data

[!include [banner](../includes/banner.md)]

As part of its standard operation, Supply Chain Management generates and stores sales history update data on an ongoing basis. Over time, a large amount of outdated sales history data may accumulate in your system, which can cause performance and functional issues when posting documents related to sales orders, such as sales order confirmations, sales packing slips, sales picking lists, and invoices. Therefore, you should set up and schedule the *Sales update history cleanup* periodic task to run at a regular interval. The task will remove all sales history update data that is no longer needed. We also recommend that you enable the *Sales history cleanup performance improvements* feature because it makes the *Sales update history cleanup* periodic task run more effectively (though you can also run the task without enabling this feature).

## Turn on the sales history cleanup performance improvements feature

The **Sales update history cleanup** periodic batch job can take a long time if it is run infrequently on environments with a high volume of sales updates. In these situations, the *Sales history cleanup performance improvements* feature can help reduce the run duration and improve reliability.

The feature improves the existing cleanup job in the following ways:

- It splits the clean-up into batches (you can change the batch size through customizations).
- It will run for a maximum of 2 hours (you can change the duration through customizations).
- Where possible, it leverages database capabilities to minimize locking contention and avoid joining transactional tables during cleanup.

After enabling the feature, the **Sales update history cleanup** batch job (**Sales and marketing \> Period tasks \> Cleanup \> Sales update history cleanup**) will run as it did before, but with better performance and for a maximum of 2 hours. This means it might need to run several times to clean up all the data for a specific retention time frame.

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Sales and marketing*
- **Feature name:** *Sales history cleanup performance improvements*

## Set up and schedule the Sales history cleanup periodic task

To set up and schedule the *Sales history cleanup* periodic task, follow these steps.

1. Analyze your business needs to find out how many days of historic sales order posting data you need to keep. We usually recommend running the cleanup task every 3 months, with a maximum of every 6 months.
1. Go to **Sales and marketing > Period tasks > Cleanup > Sales update history cleanup**.
1. The **Clean up sales update history** dialog opens. Make the following settings on the **Parameters** FastTab:
    - **Clean up** – <!-- KFM: Description needed --> Select one of the following values:
        - **Executed** – <!-- KFM: Description needed -->
        - **Executed and erroneous** – <!-- KFM: Description needed -->
        - **All** –  <!-- KFM: Description needed -->
    - **Created until** –<!-- KFM: Description needed -->
    - **Retain records based on age** –<!-- KFM: Description needed -->
    - **Maximum age** – <!-- KFM: Description needed -->
1. On the **Run in the background** FastTab, specify how, when, and how often to run the task. Use these settings to implement the schedule you decided on in step 1. The fields work just as they do for other types of [batch jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog.
