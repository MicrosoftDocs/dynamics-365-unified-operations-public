---
# required metadata

title: What's new or changed in Dynamics 365 Retail version 10.0.6
description: This topic describes features that are in preview in Dynamics 365 Retail. 
author: josaw1
ms.date: 10/09/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Release 10.0.6

---
# What's new or changed in Dynamics 365 Retail version 10.0.6

[!include [banner](../../includes/banner.md)]

This topic describes features that are new or changed in Microsoft Dynamics 365 Retail in 10.0.6. 

To learn about the features in Finance and Operations applications, see [What's new or changed in Finance and Operations apps version 10.0.6 (November 2019)](/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-6).

## New Inventory Availability API's for E-commerce use
Four new API's will be made available to provide e-commerce or 3rd party solutions with an estimation of on-hand inventory for a requested item and warehouse.  These API's are intended to replace the existing GetProductAvailabilities and GetAvailableInventoryNearby API's that are currently in-market.   These new API's will have improved calculation logic and caching to improve performance.  The names of the new API's are:
* GetEstimatedProductWarehouseAvailability
* GetEstimatedAvailabilityDefaultWarehouse
* GetEstimatedAvailabilityNearby
* GetEstimatedAvailabilityAllWarehouses

Additionally, new tables have been added for tracking available ecommerce inventory in the channel database.  Retail and Retail Shared parameters will be made available that must be configured to uptake these new API's and tables turn off the existing expensive e-commerce inventory availability logic that existed in previous versions.

### Install merchant properties deprecated from the Hardware station installer
To better support future enhancements to headless installation, the merchant properties installer has been removed from the Hardware station installation experience. New for 10.0.6, the hardware station merchant properties will be set at runtime when the POS is paired to a hardware station and updated when the hardware station is made active, if needed. If both the POS and hardware station are not updated to 10.0.6 at the same time, the setting and updating of merchant properties by POS will not function correctly. This means that if the POS is updated, but not the hardware station, then the hardware station will continue to use old merchant properties until it is updated as well. 

## Additional resources

### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]