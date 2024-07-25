---
title: Track time-series inventory in Inventory Visibility
description: This article describes how to set up Dynamics 365 Supply Chain Management inventory time-series data integration with Inventory Visibility so that you can query the projected inventory by date and calculate ATP
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Integrate Supply Chain Management ATP with Inventory Visibility

The Inventory Visibility service enables external systems to query Dynamics 365 Supply Chain Management for inventory changes occurring up to 180 days in the future. As a result, users working in an external system can view future inventory availability details and make accurate projections for when orders can be delivered. The Inventory Visibility service can import information about planned inbound and outbound inventory changes together with the related dates. Available-to-promise (ATP) functionality in Inventory Visibility can then query these time-series based inventory changes and calculate your omnichannel ATP. External systems can query and retrieve this information from Inventory Visibility in near real time by calling its API.

The *Inventory Visibility integration with ATP* feature described in this article adds support for out-of-the-box ATP integration between Supply Chain Management and Inventory Visibility. It makes it easy to bring expected inventory issue and receipts with time-series information from Supply Chain Management into Inventory Visibility, and to post updated scheduling information back to Supply Chain Management.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Inventory Visibility integration with ATP* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be running the latest version of Inventory Visibility. <!--KFM: Can we provide a required version number? --> For more information about how to install Inventory Visibility, view version information, and check for updates, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Enable Inventory Visibility integration with ATP in Supply Chain Management

To configure Supply Chain Management to exchange ATP information with Inventory Visibility, follow these steps:

1. Sign in to Dynamics 365 Supply Chain Management.
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration with ATP**.
1. On the Action Pane, select **Enable** to enable the integration. (If you ever need to disable the integration, you can select **Disable** here.)

<!--KFM: We should describe the other information provided on this page (Status, Executed date, and Records to be posted to the Inventory) -->

## Default calculated measure for ATP in Supply Chain Management

Inventory Visibility includes a default calculated measure named `@iv.@atp`, which includes all expected issues and receipts from Dynamics 365 Supply Chain Management. You'll typically use the `@iv.@atp` calculated measure to query Supply Chain Management ATP information in Inventory Visibility. You can customize it as needed. For information about how to work with calculated measures, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures).

## Set up ATP in Inventory Visibility

ATP in Inventory Visibility works the same way when integrated with Supply Chain Management as it does with other systems. For instructions on how to set up and use ATP in Inventory Visibility, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

## Work with ATP data in the Inventory Visibility app in Power Apps

You can query and post ATP information when using the Inventory Visibility app in Power Apps.

- To query ATP information, go to **Operational visibility** \> **On hand query** and be sure to enable the **Query ATP** option.
- To post ATP information, go to **Operational visibility** \> **Change schedule**, where you can specify and submit updated schedule information.

For more information, see [Use the Inventory Visibility app UI version 2](inventory-visibility-power-platform.md).

## Query and post ATP data using the Inventory Visibility API

You can query and post ATP information using the Inventory Visibility API. For details, see [Submit change schedules, change events, and ATP queries through the API](inventory-visibility-available-to-promise.md#api-urls).
