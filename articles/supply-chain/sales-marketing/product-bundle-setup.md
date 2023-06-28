---
# required metadata

title: Product Bundle setup 
description: This article describes the setup options for Revenue recognition, and their implications.
author: henrikan
ms.date: 04/28/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Customer
audience: Application User
# ms.devlang: 
ms.reviewer: kmaybach
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2023-04-30
ms.dyn365.ops.version: 8.0.4

---

# Product bundle setup
[!include [banner](../includes/banner.md)]

With the deprecation of the **Revenue Recognition** feature, a new **Product bundle** feature has been added. 

The **Product bundle** feature replaces the bundle capabilities included in the **Revenue recognition** feature. This article describes the setup and its implications.

> [!NOTE]
> When the Product bundle feature is enabled, the system will check to see if any Released products in the system have the Revenue Recognition bundle setting set to Yes. If so, the system will create a batch job automatically to upgrade this data to the new Product bundle feature set. Likewise, if sales orders exist in the system that are not cancelled and have lines on it containing Revenue recognition bundle items, these sales order lines will also be upgraded to the  Product Bundle feature set.  This is intended to provide a seamless experience as users transition from the Revenue recognition bundle functionality to the Product bundle feature set. The upgrade is done as part of a Data maintenance portal action.
> 

The Product bundle feature is enabled through Feature management. Enable this feature by turning it on in the **Feature management** workspace. It is required to turn the **Revenue recognition** feature off, before you can turn the  **Product bundle** feature on in the **Feature management** workspace.  The two feature sets are mutually exclusive.

> [!NOTE]
> Product bundle isn't supported in Commerce channels (e-commerce, POS, and call center). Items that are configured as product bundle should not be added to orders or transactions that were created in Commerce channels.

## Product bundles

Bundle items are unique released products that are set up so that they include components. This setup is done by using the bill of materials (BOM) functionality. When a product bundle item is entered on a sales order, revenue is posted for the individual components, not the product bundle item. Printed documents for the customer, sales order confirmation and invoice, reflect the product bundle item and not the components, whereas the printed documents, sales order picking list and packing slip, reflect the components only and not the product bundle item.

#### Product bundle components

The components that are included in the product bundle must be set up on the **Released products** page (**Product information management \> Products \> I Released products**). These components are released products, and they must be set up in the same manner as products that are included in a BOM. For example, a released product can be an item of either the **Item** type or the **Service** type, but it must be assigned to an item model group where the **Stocked product** option is set to **Yes**. For more information, see the setup documentation for BOM items.

The components must must also be set up with a base sales price. The product bundle revenue price will be distributed to the components, based on their revenue contribution percentages which is calculated from the base sales price of each. 

### Product bundle items

When you set up a product bundle item, you must set two fields on the **Released products** page (**Product information management \> Products \> I Released products**):

- On the **Engineer** FastTab, in the **Production type** field, the item must be set up as a BOM item.
- On the **General** FastTab, in the **Product Bundle** field, the item must be marked as a product bundle item.

The components must be then assigned to the product bundle/BOM parent item on the **BOM versions** page (go to **Product information management \> Products \> I Released products**, and then, on the Action Pane, on the **Engineer** tab, in the **BOM** group, select **BOM versions**). For more information, see the setup documentation for BOMs.

**Note - Karl please insert correct link to BOM page**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
