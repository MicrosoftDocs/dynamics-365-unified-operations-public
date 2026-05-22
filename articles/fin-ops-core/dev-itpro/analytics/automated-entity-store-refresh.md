---
title: Automated Entity store refresh
description: Learn how to enable automated Entity store refresh, including a list that outlines the process of enabling the automated refresh.
author: MilindaV2
ms.author: twheeloc
ms.topic: article
ms.date: 01/14/2026
ms.reviewer: twheeloc
ms.search.form: AutomatedEntityStoreRefresh
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
---

# Automated entity store refresh

[!include [banner](../includes/banner.md)]

## Overview

The system automates and manages the entity store refresh. Administrators don't need to schedule or monitor the entity store refresh by using the system batch schedules. The refresh operation works based on anticipated latency. This functionality is enabled in Platform update 23. As an administrator, you need to opt in to use this feature.   

## Enable automated refresh
Complete the following steps to enable automated Entity store refresh.

1. Go to **System administration** > **Set up** > **Entity store**. On the **Entity store** page, a message indicates that you can switch to the **Automated Entity store refresh** option. This option is managed by the system. An admin doesn't have to schedule or monitor the Entity store refresh.

1. Select **Switch now**.

  > [!IMPORTANT]
  > This action isn't reversible. After you switch to the **Automated Entity store refresh** option, you can't revert to the old user interface (UI) experience.

1. Select **Yes** to continue.

You now see the new experience.

:::image type="content" source="./media/entity-store-data-lake-3.JPG" alt-text="Screenshot of new UI experience.":::

After the new experience is turned on, you can define the refresh for each aggregate measurement. The following refresh options are available:

- Every hour
- Twice a day
- Once a day
- Once a week

An admin can also refresh any aggregate measurement on demand by selecting the **Refresh** button. Additional options will be added in future platform updates. These options include options for real-time refresh.

> [!IMPORTANT]
> When you enable automated refresh, the system can disable the refresh of aggregate measurements. You must revisit aggregate measurements and validate that appropriate refresh intervals are applied.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
