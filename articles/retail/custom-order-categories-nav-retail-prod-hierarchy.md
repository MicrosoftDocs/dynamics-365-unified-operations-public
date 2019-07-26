---
# required metadata

title: Display order for merchandising entities in Dynamics 365 for Retail 
description: This topic explains the concepts that are related to configuring display order for various merchandising entities in Dynamics 365 for Retail
author: ashishharchwani
manager: AnnBe
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: Category, Retail product hierarchy, Navigation hierarchy
# ROBOTS: 
audience: Application User, Merchandising manager, Catalog manager
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 268444
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Configure & control the display order for various merchandising related entities in Dynamics 365 for Retail

[!include [banner](includes/banner.md)]

Retailers consider product discovery as a primary tool for customer interaction across all retail channel. Product discoverability is easiest & quick way for Retailer’s customer to be able to discover the product via browsing thru categories, search & filtering.
This topic explains the concepts that are control the display order for various merchandising entities. 

## Overview
The existing support for sorting various merchandising related entities will be enhanced to better align with existing customer scenarios that are currently requiring extensions from our implementation partners. 

Current implementation of the sort order for Categories in Navigation hierarchy are alphabetically sorted 

The custom "Display sort order" for various merchandising entities feature will empower the merchandising manager to be able to configure the custom sort order for various merchandising entities across all end-user clients including headquarters and call centers.

### Control sort order for categories in the navigation hierarchy

With this capability, Merchandising managers can control the order of categories and the order shall be reflected across all the clients including the back-office. 

#### How to configure the display order for the categories in Retail product hierarchy? 
1.	Go to Retail > Products and categories > Retail product hierarchy.
1.	Click Edit category hierarchy.
1.	Click Edit.
1.	In the tree, expand 'ALL\Action Sports'.
1.	In the tree, expand 'ALL\Team Sports'.
1.	In the Display order field, enter a number. (This can be negative value too) 
1.	In the tree, select 'ALL\Team Sports\Soccer'.
1.	In the Display order field, enter a number.
1.	In the tree, select 'ALL\Electronics'.
1.	In the tree, expand 'ALL\Electronics'.
1.	In the Display order field, enter a number.
1.  Repeat this for any additional categories that you may want to control the order. 


#### How to configure the display order for the categories in Channel navigation hierarchy? 


Display order for channel navigation hierarchy is acknowleged in HQ across all forms - 

####


![POS with Custom sorted categories](./media/POSChannelCategoriesCustomSorted.png)


#### Note
By default this feature is turned off - more about the [Feature management] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/feature-management/feature-management-overview)

1.	Go to System administration > Workspaces > Feature management.
2.	In the list, find and select the 'Enable display order for merchandising entities'.
3.	Click Enable now.

![Enable merchandising display order from feature management](./media/ConfirmationFeatureEnabledForCustomOrderingMerchEntities.png)

### 
