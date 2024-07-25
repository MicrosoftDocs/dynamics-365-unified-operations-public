---
title: Track time-series inventory in Inventory Visibility
description: This article describes how to set up Dynamics 365 SCM inventory time-series data integration with Inventory Visibility so that you can query the projected inventory by date and calculate ATP
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Track time-series inventory in Inventory Visibility

The Inventory Visibility service enables external systems to query Supply Chain Management for inventory changes occurring up to 180 days in the future. As a result, users working in an external system can view future inventory availability details and make accurate projections for when orders can be delivered.

The Inventory Visibility service can import information about planned inbound and outbound inventory changes together with the related dates. Available-to-promise (ATP) functionality in Inventory Visibility can then query these time-series based inventory changes and calculate your omnichannel ATP. External systems can query and retrieve this information from Inventory Visibility in near real time by calling its API.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Inventory Visibility integration with ATP* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be running the latest version of Inventory Visibility. <!--KFM: Can we provide a required version number? --> For more information about how to install Inventory Visibility and check for updates, see [Install and set up Inventory Visibility](inventory-visibility-setup.md). 

## Set up ATP tracking in Inventory Visibility

### Configure Inventory Visibility integration with ATP in Supply Chain Management.

1. Sign in to Dynamics 365 Supply Chain Management.
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration with ATP**.
1. On the Action Pane, select **Enable** to enable the integration. (If you ever want to disable the integration, you can select **Disable** here.)

<!--KFM: We should describe the other information provided on this page (Status, Executed date, and Records to be posted to the Inventory) -->

### Enable feature and other settings on Inventory Visibility power app

<!--KFM: NEarly all of the information in this section seems to be a repeat of that already found in [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md). We should not repeat that here. We should just provide a link to that topic and highlight anything special here. What is special here? -->

- Log on to Inventory Visibility power app
- Go to **Feature management** > **Available to promise** > **Manage**
- On the new page, switch on Enable feature toggle and Schedule for 180 days feature. Note: In latest UI 180 ATP will be enabled by default as long as you enable the ATP feature. No worries if you cannot see ‘Schedule for 180 days’ option.
- Set **Max Schedule Period to the ATP** time fence you want, it can be 180 days maximum
- On the same page, you can also see ATP Index Set Configuration, which already has a default index set.
- Note: Except for org, site, locations which by default will be included in the partition, you need to make sure all the other dimensions that you wish to support by ATP query ‘group by’ result need to be added to the index. Such as ‘Style’ or other customized dimensions
- To modify index, click the three dots on the upper-right > see all records
- On the new index configuration page, add or delete dimensions to the index.
- For example you can add ‘style’ or other dimensions to the same index by clicking New. Assign same set number (i.e. 1) and Hierarchy sequence (i.e.3) to newly added dimension. You can also adjust the hierarchy for other dimensions
- Once done, go back to the main ATP configuration page

### Configure how ATP is calculated

<!--KFM: Same comment here as for the previous section. What is new here? We should avoid repeating steps already described in [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md) -->

- On the main ATP configuration page, you can also see **Schedule Measure**
- Default calculated measure **@iv.@atp** already includes all FnO expected issue and receipts in the formula. You can also modify the description of this measure
- Click onto **@iv.@atp** to view and update the calculated measure if needed
- On **Calculated Measure Details**, you see all Dynamics 365 SCM's expected issue and receipts are included in the formula. Since all expected issues are negative quantity when passing to IV, therefore the calculated measure here uses Addition modifier for all measure
- If need, you can click **Add New Calculated Measure details** (optional)
- (Optional) If you want to include your omnichannel (other datasources) inventory measures into ATP calculation, you can add new measure details and define its modifier as **+Addition**, or **-Subtraction**
Save your newly added measure and go back to the ATP formula page you will see your new measure being added to the calculation.

### Update configuration (mandatory)

- Once done with ATP settings in IV app, go to **Admin settings** > **Update Configuration** > log in if needed > confirm changes

## Work with ATP data in the Inventory Visibility app in Power Apps

<!--KFM: This information appears to be repeated from [Use the Inventory Visibility app UI version 2](inventory-visibility-power-platform.md) and/or [Use the Inventory Visibility app UI version 1](inventory-visibility-power-platform-v1.md). Once again, we should only describe what is new here, if anything. -->

- On Inventory Visibility power app, go to **Operational Visibility** > **On Hand query** > enter product id, org id, site and location(warehouse) information you want to query ATP.
- Note: Double-check if any additional dimensions you have included in ATP index are not included in this query. For example, if in ATP index you have colour & size. You should add colour & size here by clicking Edit Dimensions. You can leave the colour/size dimension values blank but you need to add them to query body as long as they are configured in ATP index.
- Select **Query ATP**
- To post inventory changes with date to ATP, go to **Operational Visibility** > **Change Schedule**, specify key product, dimensions, datasource, measures and quantity change date, click **Post**.

## Query and post ATP data using the Inventory Visibility API

For information about how to query or post ATP information, see [Submit change schedules, change events, and ATP queries through the API](inventory-visibility-available-to-promise.md#api-urls).