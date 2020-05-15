---
# required metadata

title: Purchase trade agreement
description: This topic describes how Planning Optimization can select vendor and lead time based on the best price or lead time found in purchase trade agreements.
author: ChristianRytt
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-5-12
ms.dyn365.ops.version: AX 10.0.12

---
# Purchase trade agreement

[!include [banner](../../includes/banner.md)]

This topic describes how Planning Optimization can select the vendor and/or lead time for a planned order based on the best price or lead time found in purchase trade agreements.

## Enable the purchase trade agreement feature

Before you can use this feature, it must be enabled on on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Master planning*
- **Feature name** - *Purchase trade agreements for Planning Optimization*

## Preapre your system to consider purchase trade agreements during master planning

To configure your system to apply Planning Optimization that considers purchase trade agreements:

1. Go to **Master planning \> Setup \> Master planning parameters**, open the **Planned orders** tab, and make the following settings in the **Vendor** group:
    - **Find trade agreement** - Set this to **Yes** to include trade agreements in your master planning.
    - **Search criterion** - Choose which aspect of each purchase trade agreement to prioritize: **Minimum lead time** or **Lowest unit price**.
1. Go to **Procurement and sourcing > Setup > Prices and discounts > Activate price/discount** and make sure **Vendor** is set to **Yes**. <!-- KFM: I put this here because it seems like a site-wide setting: is that right? Also, Vendor group, and all vendors, don't matter? -->
1. Go to **Product information management > Setup > Dimension and variant groups > Storage dimension groups** and select a storage dimension group that applies to products for which master planning should consider purchase trade agreements. Make sure that each relevant storage dimension in this group shows a check mark in the **For purchase prices** column. Repeat this step for each relevant storage dimension group. <!-- KMF: Is this specific enough regarding how to select the group and dimension? --> 

## Prepare a released product for Planning Optimization with purchase trade agreements

Once your system is prepared to allow Planning Optimization to consider purchase trade agreements, you should check to make sure that each of the products that you want to use with this feature are properly set up, as described in the following procedure.

1. Go to **Product information management > Products > Released products** and then open a target product.
1. Expand the **Purchase** FastTab and make sure no **Vendor** is assigned.
1. On the Action Pane, open the **Plan** tab and, in the **Coverage** group, select **Item coverage**. Make sure that the **Use specific setting** check box is not selected. This will ensure that your settings here won't overwrite the vendor suggested by Planning Optimization. <!-- KFM: Should we also mention overwriting the lead time here, as mentioned in the table? -->
1. Close the **Item coverage** page to return to the details page for your selected product.
1. On the Action Pane, open the **Plan** tab and, in the **Forecast** group, select **Supply forecast**. Make sure that none of the rows shown here shows a value in the **Vendor account** column.
1. Close the **Supply forecast** page to return to the details page for your selected product.
1. On the Action Pane, open the **Purchase** tab and, in the **Trade agreements** group, select **View trade agreements**. Make sure that all of the relevant trade agreements are listed here and that each of them has **Disregard lead time** set to **No** for each agreement where you want Planning Optimization to consider the lead time. <!-- KMF: Do we mean at the bottom of the page here? I was never able to add a trade agreement so I couldn't check this. Also, we do mean "Disregard lead time", not "Ignore lead time", right? -->
1. Repeat this procedure for each relevant product.

## Examples of how Planning Optimization finds vendor and lead times

The following table provides examples of how various settings made for a released product and its associated purchase agreements will affect the values found for the resulting planned purchase order to be considered by Planning Optimization. The values shown in bold in the two rightmost columns are the ones selected by Planning Optimization, while the values shown in bold-italic in the other columns indicate the setting that generated thos resulting values for each row.

<!-- KFM: We haven't mentioned "Default order settings: Lead time" or "Item coverage: Overwrite lead time" before now. Should we add these to the earlier procedure? -->

| **Released product: Vendor** | **Default order settings: Lead time** | **Item coverage: Overwrite vendor** | **Item coverage: Overwrite lead time** | **Trade agreement: Vendor** | **Trade agreement: Lead time** | **Trade agreement: Disregard lead time** | **Resulting vendor** | **Resulting lead time** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ***US001*** | ***1*** | No | No | US003 | 3 | NO | **US001** | **1** |
| US001 | 1 | ***Yes: US002*** | ***Yes: 2*** | US003 | 3 | NO | **US002** | **2** |
| *(blank)* | 1 | No | No | ***US003*** | ***3*** | NO | **US003** | **3** |
| *(blank)* | ***1*** | No | No | ***US003*** | 3 | YES | **US003** | **1** |
| *(blank)* | ***1*** | ***Yes: US002*** | No | US003 | 3 | NO | **US002** | **1** |
| *(blank)* | ***1*** | ***Yes: US002*** | No | US003 | 3 | NO | **US002** | **1** |
| *(blank)* | 1 | No | Yes: 2 | ***US003*** | ***3*** | NO | **US003** | **3** |
| *(blank)* | 1 | No | ***Yes: 2*** | ***US003*** | 3 | YES | **US003** | **2** |

## Additional resources

[Purchase agreements](../../procurement/purchase-agreements.md)

<!-- KFM: Are "purchase agreements", "trade agreements" and "purchase trade agreements" all the same thing? Can we choose just one of these terms for this topic? -->
