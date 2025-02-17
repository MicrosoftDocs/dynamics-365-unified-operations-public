---
title: Dispatch work orders
description: Learn how to dispatch work orders in Asset Management, which schedules work orders and work order jobs.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetScheduledExecution 
ms.topic: how-to
ms.date: 01/27/2025
ms.custom: 
  - bap-template
---

# Dispatch work orders

[!include [banner](../../includes/banner.md)]

The dispatch functionality in Asset Management schedules work orders and work order jobs.

## Prerequisites for the update forecasts feature (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until 10.0.43 GA -->

To use the **Update forecast** option that is described later in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.43 or later.
- The feature that is named *Adjust forecast hours to match schedule hours when work orders are dispatched* must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Dispatch a work order

To dispatch a work order, follow these steps.

1. Go to **Asset management** \> **Work orders** \> **All work orders** or **Active work orders**.
1. In the grid, select the work order that you want to dispatch.
1. On the Action Pane, on the **General** tab, select **Dispatch**.
1. In the **Schedule work order** dialog box, set the following fields:

    - **Worker** – Select the worker.
    - **Schedule hours** – If the expected work hours differ from the forecast hours, enter the number of expected work hours.
    - **Scheduled start** – Specify the start date and time.
    - **Asset**, **Tool**, and **Worker** – Set one or more of these options to *Yes* if the scheduling process should observe capacity limitations for resources of the specified type that are already scheduled on other jobs.
    - **Ignore schedule** – Set this option to *Yes* to ignore closed days in the calendar. (This option applies to assets, workers, and tools.)
    - **Ignore scheduled execution** – Set this option to *Yes* to ignore any scheduling-related limitations that were selected on the work order. Learn more in [Scheduled execution](../setup-for-work-orders/scheduled-execution.md).
    - **Verbose** – Set this option to *Yes* if you want the system to show detailed information about the scheduling process. In this case, the Action center shows detailed information about the calculated scores on the work order.
    - **Update forecast** – Set this option to *Yes* to update the forecast so that it reflects any scheduling change that you made in this dialog box.

1. Select **OK**. The work order lifecycle state is automatically updated to the **Scheduled state** value that is specified on the **Lifecycle models** page (**Asset management** \> **Setup** \> **Work orders** \> **Lifecycle models**).

> [!NOTE]
> To delete the schedule on a work order, select it, and then, on the Action Pane, on the **General** tab, select **Delete schedule**. If you delete the schedule on a work order, remember to manually update the work order lifecycle state.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
