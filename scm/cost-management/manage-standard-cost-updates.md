---
# required metadata

title: Manage standard cost updates
description: Updates to standard cost data can be managed by using two different approaches -  the one-version approach and the two-version approach. 
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CostingVersion
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 69992
ms.assetid: 468de7af-c7b5-4345-bd5a-ba3aa5a900cc
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: mguada
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage standard cost updates

[!include[banner](../includes/banner.md)]


Updates to standard cost data can be managed by using two different approaches -  the one-version approach and the two-version approach. 

The one-version approach uses a single costing version that contains all cost records. These records include the original costs and all cost updates.
The two-version approach uses one version that contains records of the original costs and a second version that contains records of all cost updates. A primary advantage of the two-version approach is the clear delineation and tracking of cost updates in a separate costing version, without affecting the original costing version. The two-version approach can be used to identify multiple incremental updates, where each incremental update has a separate costing version that contains the incremental cost records. **Example** The following example illustrates how the one-version and two-version approaches can be used for updating standard costs in a manufacturing environment. For example, updates that reflect new items or error corrections. Assume that a single costing version represents the standard costs for the current year. The identifier for this version is 2016-STD. Version 2016-STD contains the current active costs for all items. Additionally, it contains all routing-related cost categories and overhead calculation formulas that were known at the start of the year 2016. 2016-STD is the original costing version.
-   **One-version approach to cost data updates** − In the one-version approach, the original costing version 2016-STD contains all cost records. Cost updates are recorded in 2016-STD and are set to a status of ”Pending.” The pending costs can be manually entered for new purchased items, or they can be calculated for a manufactured item to reflect corrections.When the one-version approach is used, the BOM calculations do not require a fallback data source because all active costs are contained in the costing version. After the pending costs become active, the original costing version 2016-STD will again contain all the current active costs.
-   **Two-version approach to cost data updates** − The two-version approach requires an additional costing version that contains only the cost updates. The identifier for this version is 2016-STD-CHANGES. Cost updates are recorded in 2016-STD-CHANGES and are set to a status of “Pending.”With the two-version approach, the BOM calculations of pending costs for manufactured items require a fallback data source. This is because the additional costing version 2016-STD-CHANGES contains only a subset of cost data. The fallback can be expressed as the active costs or as the costing version 2016-STD, because both identify the source of cost data when it is not included in 2016-STD-CHANGES. After the pending costs become active, the costing version 2016-STD-CHANGES will contain the current active costs that reflect the updates, whereas the original costing version 2016-STD will be untouched.When the two-version approach is used, blocking policies for the original costing version should be set up to prevent updates. Identical blocking policies should be set up for the additional costing version, except for the specified from-date and the selective use of blocking policies to allow for updates. The specified from-date should be updated with each batch of changes to reflect the scheduled activation date.

This example used one additional costing version for managing updates throughout the year 2016. More than one additional costing version can be used, such as a separate version for each batch of updates. When more than one additional costing is used, the fallback must be expressed as the active costs, because the active costs are spread over multiple costing versions.




