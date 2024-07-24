---
# required metadata

title: Track FnO time-series ATP data via Inventory Visibility
description: This article describes how to set up Dynamics 365 SCM inventory time-series data integration with Inventory Visibility so that you can query the projected inventory by date and calculate ATP
author: yufeihuang
ms.date: 07/20/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: yufeihuang
ms.search.validFrom: 2024-07-20
ms.dyn365.ops.version: 10.0.41
---

# Track FnO time-series ATP data via Inventory Visibility

You can now query FnO’s expected issue and receipts inventory by date via Inventory Visibility ATP.

## Version requirement

* Dynamics 365 Supply Chain Management (Finance and Operations/FnO) - This feature is available for public preview on 10.0.41
* Follow below steps to check and upgrade your IV version to latest if needed
    1. Logging onto power platform admin center with your username & password https://admin.powerplatform.microsoft.com/
    1. Go to environment > click the IV environment ID
    1. On the environment details page > resources tab > Dynamics 365 apps
    1. Scroll down or search to find Inventory Visibility, if the status shows Update available, click on ‘Update available’, agree the terms and update
    1. You can refresh the page to see the update status

## Settings

### Enable feature and data integration on Dynamics 365 SCM

1. Log onto your Dynamics 365 SCM environment that is integrated with IV
1. Go to **Feature management** > Enable **Inventory Visibility integration with ATP** (double-check Inventory Visibility integration has been enabled during basic integration)
1. Go to **Inventory Management** > **Inventory Visibility** > **Inventory Visibility integration with ATP** > click **Enable** to turn on the data sync between Dynamics 365 SCM and IV ATP

### Enable feature and other settings on Inventory Visibility power app

* Log on to Inventory Visibility power app
* Go to **Feature management** > **Available to promise** > **Manage**
* On the new page, switch on Enable feature toggle and Schedule for 180 days feature. Note: In latest UI 180 ATP will be enabled by default as long as you enable the ATP feature. No worries if you cannot see ‘Schedule for 180 days’ option.
* Set **Max Schedule Period to the ATP** time fence you want, it can be 180 days maximum
* On the same page, you can also see ATP Index Set Configuration, which already has a default index set.
* Note: Except for org, site, locations which by default will be included in the partition, you need to make sure all the other dimensions that you wish to support by ATP query ‘group by’ result need to be added to the index. Such as ‘Style’ or other customized dimensions
* To modify index, click the three dots on the upper-right > see all records
* On the new index configuration page, add or delete dimensions to the index.
* For example you can add ‘style’ or other dimensions to the same index by clicking New. Assign same set number (i.e. 1) and Hierarchy sequence (i.e.3) to newly added dimension. You can also adjust the hierarchy for other dimensions
* Once done, go back to the main ATP configuration page

### Configure how ATP is calculated on Inventory Visibility power app

* On the main ATP configuration page, you can also see **Schedule Measure**
* Default calculated measure **@iv.@atp** already includes all FnO expected issue and receipts in the formula. You can also modify the description of this measure
* Click onto **@iv.@atp** to view and update the calculated measure if needed
* On **Calculated Measure Details**, you see all Dynamics 365 SCM's expected issue and receipts are included in the formula. Since all expected issues are negative quantity when passing to IV, therefore the calculated measure here uses Addition modifier for all measure
* If need, you can click **Add New Calculated Measure details** (optional)
* (Optional) If you want to include your omnichannel (other datasources) inventory measures into ATP calculation, you can add new measure details and define its modifier as **+Addition**, or **-Subtraction**
Save your newly added measure and go back to the ATP formula page you will see your new measure being added to the calculation.

### Update configuration (mandatory)

* Once done with ATP settings in IV app, go to **Admin settings** > **Update Configuration** > log in if needed > confirm changes

## Query and post from Inventory Visibility power app UI

* On Inventory Visibility power app, go to **Operational Visibility** > **On Hand query** > enter product id, org id, site and location(warehouse) information you want to query ATP.
* Note: Double-check if any additional dimensions you have included in ATP index are not included in this query. For example, if in ATP index you have colour & size. You should add colour & size here by clicking Edit Dimensions. You can leave the colour/size dimension values blank but you need to add them to query body as long as they are configured in ATP index.
* Select **Query ATP**
* To post inventory changes with date to ATP, go to **Operational Visibility** > **Change Schedule**, specify key product, dimensions, datasource, measures and quantity change date, click **Post**.

## Query and post data using API

The APIs used to query or post data to Inventory ATP remains unchanged. You can find all APIs here [Submit change schedules, change events, and ATP queries through the API](/dynamics365/supply-chain/inventory/inventory-visibility-setup).
