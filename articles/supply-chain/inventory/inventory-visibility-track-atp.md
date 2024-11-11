---
title: Track time-series inventory in Inventory Visibility (preview)
description: This article explains how to set up the integration of inventory time-series data in Microsoft Dynamics 365 Supply Chain Management with Inventory Visibility so that you can query the projected inventory by date and calculate ATP.
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Track time-series inventory in Inventory Visibility 

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!--KFM: Preview until further notice -->
<!--WSA: Please review preview banner, as this feature already GA -->

The Inventory Visibility service enables external systems to query Microsoft Dynamics 365 Supply Chain Management for inventory changes that will occur up to 180 days in the future. In this way, users who work in an external system can view future inventory availability details and make accurate projections about when orders can be delivered.

The Inventory Visibility service can import information about planned inbound and outbound inventory changes together with the related dates. Available-to-promise (ATP) functionality in Inventory Visibility can then query those time-series based inventory changes and calculate your omnichannel ATP. External systems can query and retrieve this information from Inventory Visibility in near-real time by calling its API.

The *Inventory Visibility integration with ATP* feature that is described in this article adds support for out-of-box ATP integration between Supply Chain Management and Inventory Visibility. Therefore, you can easily bring expected inventory issue and receipts together with time-series information from Supply Chain Management into Inventory Visibility. You can also post updated scheduling information back to Supply Chain Management.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use the feature that is described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.41 or later.
- The feature that is named *Inventory Visibility integration with ATP* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be running the latest version of Inventory Visibility. Learn how to install Inventory Visibility, view version information, and check for updates in [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Enable Inventory Visibility integration with ATP in Supply Chain Management

To configure Supply Chain Management to exchange ATP information with Inventory Visibility, follow these steps.

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration with ATP**.
1. On the Action Pane, select **Enable** to enable the integration. (If you must ever disable the integration, you can select **Disable** here.)

## Default calculated measure for ATP in Supply Chain Management

Inventory Visibility includes a default calculated measure that is named `@iv.@atp`. This calculated measure includes all expected issues and receipts from Supply Chain Management. You typically use it to query Supply Chain Management ATP information in Inventory Visibility. You can customize it as you require. Learn how to work with calculated measures in [Calculated measures](inventory-visibility-configuration.md#calculated-measures).

## Set up ATP in Inventory Visibility

When ATP in Inventory Visibility is integrated with Supply Chain Management, it works just as it does when it's integrated with other systems. Learn how to set up and use ATP in Inventory Visibility in [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

## Work with ATP data in the Inventory Visibility app in Power Apps

When you use the Inventory Visibility app in Power Apps, you can query and post ATP information.

- To query ATP information, go to **Operational visibility** \> **On hand query**. Be sure to enable the **Query ATP** option.
- To post ATP information, go to **Operational visibility** \> **Change schedule**. There, you can specify and submit updated schedule information.

Learn more in [Use the Inventory Visibility app UI version 2](inventory-visibility-power-platform.md).

## Query and post ATP data using the Inventory Visibility API

You can use the Inventory Visibility API to query and post ATP information. Learn more in [Submit change schedules, change events, and ATP queries through the API](inventory-visibility-available-to-promise.md#api-urls).
