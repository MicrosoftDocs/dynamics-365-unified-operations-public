---
title: Clean up staging data
description: Learn how to clean up the staging data tables in Supply Chain Management. The staging data tables store data that is imported from Demand planning.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/16/2025
ms.custom: 
  - bap-template
---

# Clean up staging data

[!include [banner](../includes/banner.md)]

When you import data from Demand planning into Supply Chain Management, the data is stored in staging tables in the Supply Chain Management database. After the import is complete, the staging data is no longer needed. However, after many imports, the staging tables might eventually grow to be very large, which can reduce database performance and add to data storage charges. <!-- KFM: The UI text implies that the table only grows after a failed import. Does that mean that the system automatically cleans up after each successful import? --> To avoid this problem, you can periodically clean up the staging data tables. The cleanup process deletes all data from the staging tables that is older than a specified number of days.

## Manually clean up staging data

You can manually clean up the staging data tables at any time by following these steps:

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Periodic tasks** \> **Setup** \> **Demand planning app parameters**.
1. Open the **Periodic tasks** tab. <!-- KFM: This tab is deceptively named. We are not running a periodic task here, but instead doing a one-off mandatory operation. -->
1. In the **Delete data from jobs executed before** field, enter the newest date for which you want to keep staging data. All data that is older than this date will be deleted.
1. Select **Run clean up job**.

## Automatically clean up staging data periodically

To automatically clean up staging data periodically, you can set up a batch job that runs the cleanup process at regular intervals. To do this, follow these steps:

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Periodic tasks** \> **Setup** \> **Demand planning app parameters**.
1. Open the **General** tab.
1. Set **Clean up staging data** to *Yes*. <!-- KFM: I suppose THIS is the actual periodic task? How often does it run? -->
