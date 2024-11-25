---
# required metadata

title: What's new or changed in Dynamics 365 Retail version 10.0.6
description: This article describes features that are in preview in Dynamics 365 Retail version 10.0.6. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.custom:
  - bap-template
  - evergreen
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Release 10.0.6

---
# What's new or changed in Dynamics 365 Retail version 10.0.6

[!include [banner](../../includes/banner.md)]

This article describes features that are new or changed in Microsoft Dynamics 365 Retail version 10.0.6. 

To learn about the features in finance and operations applications, see [What's new or changed in finance and operations apps version 10.0.6 (November 2019)](/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-6).

## New Inventory Availability APIs for E-commerce use
Four new APIs will be made available to provide e-commerce or third party solutions with an estimation of on-hand inventory for a requested item and warehouse.  These APIs are intended to replace the existing GetProductAvailabilities and GetAvailableInventoryNearby APIs that are currently in-market. These new APIs will have improved calculation logic and caching to improve performance. The names of the new APIs are:
* GetEstimatedProductWarehouseAvailability
* GetEstimatedAvailabilityDefaultWarehouse
* GetEstimatedAvailabilityNearby
* GetEstimatedAvailabilityAllWarehouses

Additionally, new tables have been added for tracking available ecommerce inventory in the channel database. Retail and Retail Shared parameters will be made available that must be configured to uptake these new APIs and tables turn off the existing expensive e-commerce inventory availability logic that existed in previous versions.

### Install merchant properties deprecated from the Hardware station installer
To better support future enhancements to headless installation, the merchant properties installer has been removed from the Hardware station installation experience. New for 10.0.6, the hardware station merchant properties will be set at runtime when the POS is paired to a hardware station and updated when the hardware station is made active, if needed. If both the POS and hardware station aren't updated to 10.0.6 at the same time, the setting and updating of merchant properties by POS won't function correctly. This means if the POS is updated, but not the hardware station, the hardware station will use old merchant properties until it's updated. 

## Additional resources

### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
