---
# required metadata

title: Items where used
description: This topic explains how to find where items have been used in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Items where used

This topic explains how to find where items have been used in Enterprise Asset Management. You can make a calculation for a specific item to get an overview of where in Enterprise Asset Management the item has been used. The results show the context in which the item has been used during its lifetime. The Item where used form can be opened from the main Enterprise asset management menu, and it can also be accessed from the following grid views and detail views:

[Object BOM](../objects/object-BOM.md)

[Spare parts](../setup-for-objects/object-types.md)

[Object type setup](../setup-for-objects/object-types.md)

[Job type setup forecast](../setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md)

[Work order forecast](../work-orders/forecasts.md)

[Work order purchase requisition](../work-orders/procurement.md)

[Work order purchase](../work-orders/procurement.md)

## Make an item where used calculation

1. Click **Enterprise asset management** > **Inquiries** > **Item where used**, or select the **Item where used** button in one of the views mentioned above.

2. Click **Item where used** > **Calculate where used**.

3. Select the item for which you want to make the calculation in the **Item number** field.

4. You can use the **Level** field to indicate how detailed you want the item lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location hierarchy, all item lines for a functional location will be shown on the top level. Therefore, relation/quantity on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you will see a detailed result showing all item lines on all the functional location levels to which they are related.

5. In the **Include** section, select the check boxes for the various parts in Enterprise asset management that you want to include in the calculation.

6. Click **OK** to start the calculation.

7. On the **Item where used** tab > the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane group buttons are highlighted in blue color. Click on a button to activate or deactivate it.

8. If you want to show dimensions related to the item, click **Dimensions display**, and select the dimensions to be shown.

The figure below shows a screenshot of the interface.

![Figure 1](media/16-controlling-and-reporting.png)
