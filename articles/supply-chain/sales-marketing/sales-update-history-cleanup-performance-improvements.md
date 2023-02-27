---
title: Schedule sales history data cleanup
description: This article describes how you can help improve system performance by scheduling the Sales update history cleanup periodic task to run at a regular interval.
author: myvakalo
ms.date: 08/09/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-09-29
ms.dyn365.ops.version: 10.0.19
---

# Schedule sales history data cleanup

[!include [banner](../includes/banner.md)]

As part of its standard operation, Microsoft Dynamics 365 Supply Chain Management generates and stores sales history update data on an ongoing basis. Over time, a large amount of outdated sales history data might accumulate in your system. This accumulated data can cause performance and functional issues when documents that are related to sales orders are posted. (These documents include sales order confirmations, sales packing slips, sales picking lists, and invoices). Therefore, you should set up and schedule the *Sales update history cleanup* periodic task to run at a regular interval. This task will remove all sales history update data that is no longer needed.

If you use the *Sales update history cleanup* periodic task, we recommend that you enable the *Sales history cleanup performance improvements* feature, which makes the task run more effectively. (Nevertheless, you can also run the task without enabling this feature.)

## Turn on the sales history cleanup features

To set up and use the *Sales update history cleanup* periodic task together with all the features that are described in this article, you must enable the *Sales history cleanup performance improvements* and *Clean up sales update history based on age* features in Feature management, as described in the following subsections.

### Sales history cleanup performance improvements

The **Sales update history cleanup** periodic batch job can take a long time if it is run infrequently on environments with a high volume of sales updates. In these situations, the *Sales history cleanup performance improvements* feature can help reduce the run duration and improve reliability.

The feature improves the existing cleanup job in the following ways:

- It splits the clean-up into batches (you can change the batch size through customizations).
- It will run for a maximum of 2 hours (you can change the duration through customizations).
- Where possible, it leverages database capabilities to minimize locking contention and avoid joining transactional tables during cleanup.

After enabling the feature, the **Sales update history cleanup** batch job (**Sales and marketing \> Period tasks \> Cleanup \> Sales update history cleanup**) will run as it did before, but with better performance and for a maximum of 2 hours. This means it might need to run several times to clean up all the data for a specific retention time frame.

Before you can use this feature, it must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Sales and marketing*
- **Feature name:** *Sales history cleanup performance improvements*

### Clean up sales update history based on age

The *Clean up sales update history based on age* feature lets you specify the maximum age of records to keep when the *Sales update history cleanup* periodic task is run. Older records will be deleted. This feature is useful when you set up the task to run periodically, because the age is always calculated relative to the date when the task is run. If you don't use this feature, you can only set a specific date for the oldest records to keep.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Clean up sales update history based on age* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set up and schedule the Sales history cleanup periodic task

To set up and schedule the *Sales history cleanup* periodic task, follow these steps.

1. Analyze your business needs to determine how many days of historic sales order posting data you must keep. We usually recommend that you run the cleanup task every three months and a maximum of every six months.
1. Go to **Sales and marketing \> Period tasks \> Cleanup \> Sales update history cleanup**.
1. In the **Clean up sales update history** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Clean up** – Select one of the following values to specify the type of records to clean up:

        - **Executed** – Delete only records that have been fully processed. Because you're unlikely to have any further use for these records, this option is the safest.
        - **Executed and erroneous** – Delete both fully processed records and records where an error has occurred. This option is the most commonly used. You might want to inspect and even fix erroneous records instead of having them automatically cleaned up. However, many companies choose to clean up these records too after about a month, because they are probably no longer relevant by that time.
        - **All** – Delete executed, erroneous, and waiting records. Waiting records are valid but haven't yet been fully processed. In most cases, you probably don't want them to be deleted automatically. However, in some situations, you might choose to have them automatically deleted after a specific amount of time has passed.

    - **Retain records based on age** – Specify whether you want to clean up records based on their age on the day when the task is run or delete records that were created before a fixed date. If you're scheduling the cleanup as a recurring task, you should set this option to *Yes*, because the age is always calculated relative to the date when the task is run.

        - Set this option to *Yes* to enable the **Maximum age** field. You use this field to specify the maximum age of the records to keep each time that the task is run. The **Created until** field is ignored.
        - Set this option to *No* to enable the **Created until** field. You use this field to specify the oldest creation date of the records to keep when the task is run. The **Maximum age** field is ignored.

    - **Created until** – This setting applies only when the **Retain records based on age** option is set to *No*. Specify the oldest creation date of the records to keep when the task is run. Records that were created before this date will be deleted.
    - **Maximum age** – This setting applies only when the **Retain records based on age** option is set to *Yes*. Specify the maximum age (in days) of the records to keep each time that the task is run. Older records will be deleted.

1. On the **Run in the background** FastTab, specify how, when, and how often the task is run. Use these settings to implement the schedule that you determined in step 1. The fields work just as they do for other types of [batch jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box.
