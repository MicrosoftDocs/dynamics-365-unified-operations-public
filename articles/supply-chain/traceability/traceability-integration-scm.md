---
title: Integrate Traceability with Supply Chain Management (preview)
description: Learn how to integrate the Traceability add-in for Dynamics 365 Supply Chain Management with Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Integrate Traceability with Supply Chain Management (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Traceability add-in for Dynamics 365 Supply Chain Management provides out-of-box integration with manufacturing execution features of Dynamics 365 Supply Chain Management. <!--KFM: Demo data implies support for received purchases. Mention that here? -->

Shop floor operators using the [production floor execution interface](../production-control/production-floor-execution-use.md) can associate the unique ID (serial/batch number) of finished products with the unique ID (serial/batch number) of raw materials. This association is integrated into Traceability for insight processing. Managers can also use the web client to view and register serial and batch number information for components and finished goods.

## Prerequisites

To integrate Traceability with Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *(Preview) Supply Chain Traceability*
    - *Tracked components*

## Configure activities in Traceability

You must configure Traceability to recognize the activity codes submitted by Supply Chain Management. Follow these steps.

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Settings** \> **Activity**.
1. The **Activity** page opens. Make sure the following activity codes are available. For more information about these settings, see [Configure the Traceability app in Power Apps (preview)](traceability-app-configure.md)

    | Source activity code | Source activity type | Integration Scenario |
    |--|--|--|
    | PurchaseGoodsReceipt | Purchase | Purchase order goods received. |
    | ProductionReportFinished | Production | Components consumed during manufacturing assembly. |
    | ProductionPickingList | Production | Finished goods produced during production.|

    <!--KFM: Should we keep PurchaseGoodsReceipt here? -->

1. On the toolbar, select **Save**.

## Configure Supply Chain Management

You must set up your Supply Chain Management system to record batch/serial numbers for raw materials and finished goods. The following table summarizes the configuration settings you should be using.

| Configuration | Instructions | Expected Results |
|-------------------------|-------------------------|-------------------------|
| Set up a number sequence code for **Product component match ID**. | Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Number sequences** tab.</br></br>Set up a number sequence code for **Product component match ID**. | **Product component match ID** has number sequence code assigned.<!--KFM: Explain why we need this --> |
| Enable tracked components for bills of materials. | Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Bills of materials** tab.</br></br>Set **Enable tracked components** to *Yes*. | **Enable tracked components** is set to *Yes*.<!--KFM: Explain why we need this --> |
| Deactivate **On physical update** for relevant tracking number groups. | Go to **Inventory management** \> **Setup** \> **Dimensions** \> **Tracking number groups**.</br></br>Set **On physical update** to *No* for each tracking number group that is related to production orders that you want to trace using Traceability <!--KFM: Review/improve this description -->.</br></br>If you are using *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md), then do this for the *BatchAuto* and *SerialAuto* tracking number groups. | Serial and batch numbers of finished goods will be generated automatically each time you release a production or batch order. |
| Verify **Serial number control** configuration for relevant tracking dimension groups. | Go to **Product information management** \> **Setup** \> **Dimension and variant groups** \> **Tracking dimension groups** and expand the **Serial numbers** FastTab.</br></br>Set **Serial number control** to *Yes* for each tracking dimension group that applies to serial numbers used in production. <!--KFM: Review/improve this description. What about batch numbers? --></br></br>If you are using *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md), then do this for the *SerialProd* tracking dimension group. | When raw material is received, a corresponding serial number will be registered.</br></br>You can see these numbers by going to **Inventory management** \> **Inquires and reports** \> **Tracking dimensions** \> **Serial numbers**. |
| Set **Registration error mode** to *Auto correct*. | Go to **Time and attendance** \> **Setup** \> **Time and attendance parameters** and open the **General** tab.</br></br>Set **Registration error mode** to *Auto correct*. | <!--KFM: Explain why we need this. Or maybe this is just for the sample scenario? --> |
| Add the *Tracked components* action to relevant areas of the production floor execution interface | Go to **Production control** \> **Setup** \> **Manufacturing execution** \> **Configure production floor execution**.</br></br>Select a relevant configuration and, from the Action Pane, select **Design tabs**. Add the *Tracked components* action to each relevant tab and toolbar. Repeat this for each relevant configuration</br></br>If you are using *USMF* [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md), then open the **Default** configuration, select the *Active jobs* design tab and add the *Tracked components* action to the **Primary toolbar**.</br></br>For more information about these settings, see [Design the production floor execution interface](../production-control/production-floor-execution-tabs.md). | The **Tracked components** action is now available to workers in the production floor execution interface. |

<!-- KFM: Notes:

- I removed rows from above table that related to setting up PFE users and badge ID. That's not specific to Traceability. We could link to [Set up worker accounts to use the production floor execution interface](../production-control/production-floor-execution-worker-accounts.md) needed.

- I likewise removed the longer scenario from this topic because it includes too much setup and demo of features not directly related to Traceability. We could consider creating a Learn module for that scenario. Please let me know if you disagree. 

-->

## Register and view batch/serial numbers for finished products and their components

Workers can register batch/serial numbers for finished products and their components from the production floor execution interface. For details, see [Register batch/serial numbers for finished products and their components](../production-control/production-floor-execution-use.md#tracked-components).

Managers can register and review batch/serial numbers for finished products and their components using the Supply Chain Management web client. For details, see [Register and track batch/serial numbers for finished products and their components](../production-control/tracked-components.md).
