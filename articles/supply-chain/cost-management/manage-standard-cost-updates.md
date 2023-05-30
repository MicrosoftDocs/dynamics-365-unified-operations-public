---
# required metadata

title: Manage standard cost updates
description: Updates to standard cost data can be managed by using two different approaches - the one-version approach or the two-version approach. 
author: JennySong-SH
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostingVersion, InventItemPrice, InventParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 468de7af-c7b5-4345-bd5a-ba3aa5a900cc
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: 10.0.17
---

# Manage standard cost updates

[!include [banner](../includes/banner.md)]

Updates to standard cost data can be managed by using two different approaches - the one-version approach or the two-version approach.

The one-version approach uses a single costing version that contains all cost records. These records include the original costs and all cost updates.

The two-version approach uses one version that contains records of the original costs and a second version that contains records of all cost updates. A primary advantage of the two-version approach is the clear delineation and tracking of cost updates in a separate costing version, without affecting the original costing version. The two-version approach can be used to identify multiple incremental updates, where each incremental update has a separate costing version that contains the incremental cost records.

## Example

The following example illustrates how the one-version and two-version approaches can be used for updating standard costs in a manufacturing environment. For example, updates that reflect new items or error corrections. Assume that a single costing version represents the standard costs for the current year. The identifier for this version is 2020-STD. Version 2020-STD contains the current active costs for all items. Additionally, it contains all routing-related cost categories and overhead calculation formulas that were known at the start of the year 2020. 2020-STD is the original costing version.

- **One-version approach to cost data updates** − In the one-version approach, the original costing version 2020-STD contains all cost records. Cost updates are recorded in 2020-STD and set to a status of Pending. The pending costs can be manually entered for new purchased items, or they can be calculated for a manufactured item to reflect corrections. When the one-version approach is used, the BOM calculations do not require a fallback data source because all active costs are contained in the costing version. After the pending costs become active, the original costing version 2020-STD will again contain all the current active costs.
- **Two-version approach to cost data updates** − The two-version approach requires an additional costing version that contains only the cost updates. The identifier for this version is 2020-STD-CHANGES. Cost updates are recorded in 2020-STD-CHANGES and are set to a status of Pending. With the two-version approach, the BOM calculations of pending costs for manufactured items require a fallback data source. This is because the additional costing version 2020-STD-CHANGES contains only a subset of cost data. The fallback can be expressed as the active costs or as the costing version 2020-STD, because both identify the source of cost data when it is not included in 2020-STD-CHANGES. After the pending costs become active, the costing version 2020-STD-CHANGES will contain the current active costs that reflect the updates, whereas the original costing version 2020-STD will not be affected. When the two-version approach is used, blocking policies for the original costing version should be set up to prevent updates. Identical blocking policies should be set up for the additional costing version, except for the specified from-date and the selective use of blocking policies to allow for updates. The specified from-date should be updated with each batch of changes to reflect the scheduled activation date.

This example used one additional costing version for managing updates throughout the year 2020. More than one additional costing version can be used, such as a separate version for each batch of updates. When more than one additional costing is used, the fallback must be expressed as the active costs, because the active costs are spread over multiple costing versions.

## Financial dimensions for the standard cost revaluation

Activating a new standard price will typically revaluate the on-hand inventory value by standard cost revaluation transactions. Usually, the financial dimensions of the item are then posted on the transactions. However, if you would like to control whether and how the financial dimensions are posted, use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn on the feature named *Options of defaulting financial dimensions for inventory standard cost revaluation*. After enabling this feature, go to **Cost management > Inventory accounting policies setup > Parameters** and set the new **Origin of financial dimension** drop-down list to one of the following values:

- **None** – No financial dimensions are posted on the revaluation transactions. If your account structure includes a required financial dimension, the revaluation process will still run, but it will create accounting entries that have no financial dimensions. In this case, users will receive a warning message first, so they can cancel the revaluation if necessary.
- **Table**  – The financial dimensions of the item are posted on the revaluation transactions. This is the default setting and is consistent with the original system behavior without turning on the feature *Options of defaulting financial dimensions for inventory standard cost revaluation*.
- **Posting** – The financial dimensions of the transaction that is being revalued are posted on the revaluation transactions. By default, the financial dimensions from the original transaction's inventory account will be used for both the inventory account and the revaluation account.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]