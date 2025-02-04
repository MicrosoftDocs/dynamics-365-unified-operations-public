---
title: Integrate Traceability with tracked components in Supply Chain Management (preview)
description: Learn how to integrate the Traceability Add-in for Dynamics 365 Supply Chain Management with the tracked components feature in Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Integrate Traceability with tracked components in Supply Chain Management (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Traceability Add-in for Dynamics 365 Supply Chain Management provides out-of-the-box integration with the tracked components feature in Dynamics 365 Supply Chain Management.

Shop floor operators using the [production floor execution interface](../production-control/production-floor-execution-use.md) can associate the unique ID (serial/batch number) of finished products with the unique ID (serial/batch number) of raw materials. This association is integrated into Traceability for insight processing. Managers can also use the Supply Chain Management web client to [view and register serial and batch number information](../production-control/tracked-components.md) for components and finished goods.

## Prerequisites

To integrate Traceability with the tracked components feature Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *(Preview) Traceability*
    - *Tracked components*

## Configure activities in Traceability

You must configure Traceability to recognize the activity codes submitted by Supply Chain Management. Follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens. Make sure the following activity codes are available. For more information about these settings, see [Configure Traceability](developer/traceability-configure.md).

    | Source activity code | Source activity type | Integration Scenario |
    |--|--|--|
    | ProductionReportFinished | Production | Components consumed during manufacturing assembly. |
    | ProductionPickingList | Production | Finished goods produced during production.|

1. On the toolbar, select **Save**.

## Configure Supply Chain Management

You must set up your Supply Chain Management system to record batch/serial numbers for raw materials and finished goods. The following procedure summarizes the configuration settings you should be using.

1. Set up a number sequence code for *Product component match ID*.

    1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Number sequences** tab.
    1. Set up a number sequence code for *Product component match ID*.

1. Enable tracked components for bills of materials.

    1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Bills of materials** tab.
    1. Set **Enable tracked components** to *Yes*.

1. Add the *Tracked components* action to relevant areas of the production floor execution interface.

    1. Go to **Production control** \> **Setup** \> **Manufacturing execution** \> **Configure production floor execution**.
    1. Select a relevant configuration and, from the Action Pane, select **Design tabs**. Add the *Tracked components* action to each relevant tab and toolbar. Repeat this step for each relevant configuration.

    If you're using *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md), then open the **Default** configuration, select the *Active jobs* design tab, and add the *Tracked components* action to the **Primary toolbar**.

    For more information about these settings, see [Design the production floor execution interface](../production-control/production-floor-execution-tabs.md).

## Register and view batch/serial numbers for finished products and their components

Workers can register batch/serial numbers for finished products and their components from the production floor execution interface. For details, see [Register batch/serial numbers for finished products and their components](../production-control/production-floor-execution-use.md#tracked-components).

Managers can register and review batch/serial numbers for finished products and their components using the Supply Chain Management web client. For details, see [Register and track batch/serial numbers for finished products and their components](../production-control/tracked-components.md).
