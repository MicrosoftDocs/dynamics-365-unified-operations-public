---
# required metadata

title: Master planning with purchase trade agreements
description: This topic describes how Planning Optimization can find the vendor and/or lead time for a planned order based on the best price or lead time found in purchase trade agreements.
author: ChristianRytt
manager: tfehr
ms.date: 05/29/2020
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
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: AX 10.0.12

---
# Master planning with purchase trade agreements

[!include [banner](../../includes/banner.md)]

This topic describes how Planning Optimization can find the vendor and/or lead time for a planned order based on the best price or lead time found among all purchase trade agreements specified for a given product.

## Enable the purchase trade agreements for Planning Optimization feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Master planning*
- **Feature name** - *Purchase trade agreements for Planning Optimization*

## Prepare your system to evaluate purchase trade agreements during master planning

To configure your system to apply Planning Optimization that evaluates purchase trade agreements:

1. Go to **Master planning \> Setup \> Master planning parameters**, open the **Planned orders** tab, and make the following settings in the **Vendor** group:
    - **Find trade agreement** - Set this to **Yes** to include purchase trade agreements in your master planning.
    - **Search criterion** - Choose which aspect of each purchase trade agreement to prioritize: **Minimum lead time** or **Lowest unit price**.
1. Go to **Procurement and sourcing > Setup > Prices and discounts > Activate price/discount** and make sure **Vendor** is set to **Yes**.
1. Go to **Product information management > Setup > Dimension and variant groups > Storage dimension groups** and select a storage dimension group that applies to products for which master planning should evaluate purchase trade agreements. Make sure that each relevant storage dimension in this group shows a check mark in the **For purchase prices** column. Repeat this step for each relevant storage dimension group.

## Prepare a released product to evaluate purchase trade agreements during master planning

Once your system is prepared as described previously, you should check to make sure that each of the products that you want to use with this feature is properly set up, as described in the following procedure.

1. Go to **Product information management > Products > Released products** and then open a target product.

1. Expand the **Purchase** FastTab and make sure no **Vendor** is assigned.

1. On the Action Pane, open the **Plan** tab and, in the **Coverage** group, select **Item coverage** to open the **Item coverage** page for your selected product. Check the following settings:

    - On the **General** tab, you are able to set up vendor overrides. You should disable vendor overrides if you want to allow Planning Optimization to use purchase trade agreements to select a vendor. To prevent vendor overrides, clear the **Use specific setting** check box.
    - On the **Lead time** tab, you are able to set up lead-time overrides. You should disable these if you want to allow Planning Optimization to use purchase trade agreements to select lead times. To prevent lead-time overrides, clear the check box for each type of lead time that you want to select using purchase trade agreements (**Purchase**, **Production**, and/or **Transfer**).

1. Close the **Item coverage** page to return to the details page for your selected product.

1. On the Action Pane, open the **Plan** tab and, in the **Forecast** group, select **Supply forecast**. Make sure that none of the rows shown here shows a value in the **Vendor account** column.

1. Close the **Supply forecast** page to return to the details page for your selected product.

1. On the Action Pane, open the **Purchase** tab and, in the **Trade agreements** group, select **View trade agreements**. Make sure that all of the relevant purchase trade agreements are listed here and that each of them has **Disregard lead time** set to **No** for each agreement where you want Planning Optimization to use the lead time specified for that agreement.

1. On the Action Pane, open the **Plan** tab and, in the **Order settings** group, select **Default order settings** to open the **Default order settings** page for your selected product. Expand the **Purchase order** FastTab and check the value shown there for **Purchase lead time**. Planning Optimization will use this value (provided no item coverage override lead time is defined) when selecting trade agreements where **Disregard lead time** is set to **Yes**, so adjust it if needed.

1. Repeat this procedure for each relevant product.

## Examples of how Planning Optimization finds vendor and lead times

The following table provides examples of how various settings made for a released product and its associated purchase trade agreements will affect the values found for the resulting planned purchase order. The values shown in bold in the two rightmost columns are the ones selected by Planning Optimization, while the values shown in bold-italic in the other columns indicate the setting that produced those resulting values for each row.

| **Released product: Vendor** | **Default order settings: Lead time** | **Item coverage: Override vendor** | **Item coverage: Override lead time** | **Trade agreement: Vendor** | **Trade agreement: Lead time** | **Trade agreement: Disregard lead time** | **Resulting vendor** | **Resulting lead time** |
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
