---
title: Dispatch work order
description: Learn how to dispatch a work order in Asset Management, which schedules work orders and work order jobs, including a step-by-step process.
author: jodahlMSFT
ms.author: jodahl
ms.topic: article
ms.date: 12/11/2024
ms.custom:
ms.reviewer: kamaybac
ms.search.form: EntAssetScheduledExecution 
---

# Dispatch work order

[!include [banner](../../includes/banner.md)]

The dispatch functionality in Asset Management schedules work orders and work order jobs.

## Prerequisites for the update forecasts feature (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until 10.0.43 GA -->

To use the **Update forecast** option described later in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.43 or later.
- The feature that is named *Adjust forecast hours to match schedule hours when work orders are dispatched* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Dispatch a work order

To dispatch a work order, follow these steps:

1. Go to **Asset management** \> **Work orders** \> **All Work orders** or **Active work orders**.
1. On the grid, select the work order you want to dispatch.
1. On the Action Pane, open the **General** tab and select **Dispatch**.
1. In the **Schedule work order** dialog, make the following settings:
    - **Worker** – Select the worker.
    - **Schedule hours** – If the expected work hours differ from the forecast hours, enter the number of expected work hours.
    - **Scheduled start** – Edit start date and time, if required.
    - **Asset**, **Tool**, and **Worker** – Set one or more of these to *Yes* if the scheduling process should observe capacity limitations regarding resources of the specified type that are already scheduled on other jobs.
    - **Ignore schedule** – Set to *Yes* to ignore closed days in the calendar (applies to assets, workers, and tools).
    - **Ignore scheduled execution** – Set to *Yes* to ignore limitations that may have been selected on the work order regarding scheduling. Learn more in [Scheduled execution](../setup-for-work-orders/scheduled-execution.md).
    - **Verbose** – Set to *Yes* to see detailed information about the scheduling process. This detailed information about the calculated scores on the work order is shown in the Action center.
    - **Update forecast** – Set to *Yes* to update the forecast to reflect any scheduling change you have made in this dialog.

1. Select **OK**. The work order lifecycle state is automatically updated to **Scheduled state** specified on the **Lifecycle models** page (available at **Asset management** \> **Setup** \> **Work orders** \> **Lifecycle models**).

[!NOTE]
If you want to delete the schedule on a work order, select it and then, on the Action Pane, open the **General** tab and select **Delete schedule**. Remember to manually update the work order lifecycle state if you delete the schedule.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
