---
title: Integrate Traceability with Supply Chain Management (preview)
description: Learn how to integrate the Traceability Add-in for Dynamics 365 Supply Chain Management with the tracked components feature in Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 08/29/2025
ms.custom: 
  - bap-template
---

# Integrate Traceability with Supply Chain Management (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Traceability can integrate seamlessly with Dynamics 365 Supply Chain Management through configuration only.

## Integrate Traceability with the purchase goods receipt

The Traceability Add-in for Dynamics 365 Supply Chain Management provides out-of-the-box integration with the purchase goods receipt in Supply Chain Management.

### Prerequisites for integrating with the purchase goods receipt

To integrate Traceability with the purchase goods receipt, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The *(Preview) Traceability* feature must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

### Configure activities in Traceability for integrating with the purchase goods receipt

You must configure Traceability to recognize the activity codes that Supply Chain Management submits. Follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens. Make sure the following activity codes are available. Learn more in [Configure Traceability](developer/traceability-configure.md).

    | Source activity code | Source activity type | Integration Scenario |
    |--|--|--|
    | PurchaseGoodsReceipt | Purchase | Product receipt of purchase order |

1. On the toolbar, select **Save**.

### Post product receipts of purchase orders

When you post a purchase order product receipt for batch‑managed or serialized products in Supply Chain Management, the system automatically sends the corresponding goods receipt event to Traceability.

## Integrate Traceability with tracked components in Supply Chain Management

The Traceability Add-in for Dynamics 365 Supply Chain Management provides out-of-the-box integration with the tracked components feature in Dynamics 365 Supply Chain Management.

Shop floor operators using the [production floor execution interface](../production-control/production-floor-execution-use.md) can associate the unique ID (serial or batch number) of finished products with the unique ID (serial or batch number) of raw materials. This association is integrated into Traceability for insight processing. Managers can also use the Supply Chain Management web client to [view and register serial and batch number information](../production-control/tracked-components.md) for components and finished goods.

### Prerequisites for integrating with tracked components

To integrate Traceability with the tracked components feature Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *(Preview) Traceability*
    - *Tracked components* (As of Supply Chain Management version 10.0.45, this feature is turned on by default.)

### Configure activities in Traceability for integrating with tracked components

You must configure Traceability to recognize the activity codes that Supply Chain Management submits. Follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens. Make sure the following activity codes are available. For more information about these settings, see [Configure Traceability](developer/traceability-configure.md).

    | Source activity code | Source activity type | Integration Scenario |
    |--|--|--|
    | ProductionReportFinished | Production | Components consumed during manufacturing assembly. |
    | ProductionPickingList | Production | Finished goods produced during production.|

1. On the toolbar, select **Save**.

### Configure Supply Chain Management to record batch and serial numbers

Set up your Supply Chain Management system to record batch and serial numbers for raw materials and finished goods. The following procedure summarizes the configuration settings you should use.

1. Set up a number sequence code for *Product component match ID*.

    1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Number sequences** tab.
    1. Set up a number sequence code for *Product component match ID*.

1. Enable tracked components for bills of materials.

    1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Bills of materials** tab.
    1. Set **Enable tracked components** to *Yes*.

1. Create tracked component policy.

    1. Go to **Production control** \> **Setup** \> **Production** \> **Tracked components policy**.
    1. Create a **Tracked components policy**.
    1. Set **Use tracked components** to *Yes*.
  
1. Associate the tracked component policy to finished products and components.

    1. Go to **Product information management** \> **Products** \> **Released products** .
    1. Open the product you want to set up.
    1. On the **Manage inventory** FastTab, set **Tracked components policy** to the name of the tracked components policy you created earlier.

1. Add the *Tracked components* action to relevant areas of the production floor execution interface.

    1. Go to **Production control** \> **Setup** \> **Manufacturing execution** \> **Configure production floor execution**.
    1. Select a relevant configuration and, from the Action Pane, select **Design tabs**. Add the *Tracked components* action to each relevant tab and toolbar. Repeat this step for each relevant configuration.

    If you're using *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md), open the **Default** configuration, select the *Active jobs* design tab, and add the *Tracked components* action to the **Primary toolbar**.

    For more information about these settings, see [Design the production floor execution interface](../production-control/production-floor-execution-tabs.md).

### Register and view batch and serial numbers for finished products and their components

Workers can register batch and serial numbers for finished products and their components from the production floor execution interface. For details, see [Register batch/serial numbers for finished products and their components](../production-control/production-floor-execution-use.md#tracked-components).

Managers can register and review batch and serial numbers for finished products and their components by using the Supply Chain Management web client. For details, see [Register and track batch/serial numbers for finished products and their components](../production-control/tracked-components.md).

## Integrate Traceability with sales goods issues

The Traceability Add-in for Dynamics 365 Supply Chain Management provides out-of-the-box integration with sales goods issues in Supply Chain Management.

### Prerequisites for integrating with sales goods issues

To integrate Traceability with sales goods issues, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.46 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *(Preview) Traceability*

### Configure activities in Traceability for integrating with sales goods issues

You must configure Traceability to recognize the activity codes that Supply Chain Management submits. Follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens. Make sure the following activity code is available. Learn more in [Configure Traceability](developer/traceability-configure.md).

    | Source activity code | Source activity type | Integration Scenario |
    |--|--|--|
    | SalesGoodsIssue | Sales | Post packing slip of sales order |

1. On the toolbar, select **Save**.

### Post packing slips of sales orders

When you post a sales order packing slip for a batch‑managed or serialized product in Supply Chain Management, the system automatically sends the corresponding goods issue event to Traceability.
