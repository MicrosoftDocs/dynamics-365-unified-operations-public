---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (December 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1.3. This version was released in December 2018.
author: tonyafehr
manager: AnnBe
ms.date: 11/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: b364a31d-34de-45c5-b698-64c5262c592e
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-11-02 
ms.dyn365.ops.version: Release 8.1.3

---
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1.3 (December 2018)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1.3. This version was released in December 2018 and has a build number of XXXXX.

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [What's new or changed in Dynamics 365 for Retail](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new).

### Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

## Bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 22, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2037783) (**not yet available**).

## Platform update 22
Microsoft Dynamics 365 for Finance and Operations version 8.1.3 includes Platform update 22. To learn more about Platform update 22, see 
[What's new or changed in Dynamics 365 for Finance and Operations platform update 22 (November 2018)](whats-new-platform-update-22.md).

## Catch weight
This functionality will provide support for using catch weight products within warehouse management processes. Catch weight products are often used in industries where products vary by weight and/or size,  such as the food industry. Catch weight products use two unit of measures   - an inventory unit (kg, lb, oz, etc. ) and a catch weight unit (box, each, pallet, etc.). The inventory unit is the unit of measure in which the product is weighed and invoiced. The catch weight unit is the unit in which the products are handled, such as received, transferred, and shipped.
Within the warehouse management processes, the catch weight products can be handled in different units, such as pallets and boxes, and the business processes can be granularly defined to, for example, perform the inbound weighing per pallet level and capture the outbound sales process during picking or packing per catch weight quantity (box).
This feature also allows you to use a catch weight tag that will get the captured   weight per catch weight unit assigned. The goal of this approach is to weigh the product only once at the time of receipt. This works for products that do not change weight over time (e.g., frozen shrimp) and products that have a handling unit of measure that is shippable (e.g., a box of shrimp). With this approach, the user scans the catch weight tag to identify the weight at the time of picking or packing based on product configuration and then invoicing is based on the weight that is associated with the captured catch weight tag. 

