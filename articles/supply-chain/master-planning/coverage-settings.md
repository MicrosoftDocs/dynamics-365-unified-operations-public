---
# required metadata

title: Coverage settings
description: This topic provides information about the coverage settings that master scheduling uses to calculate item requirements.
author: t-benebo
ms.date: 09/13/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqGroup, ReqItemTable, ReqItemTableWizard, ReqItemTableSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2494
ms.assetid: 5a95ae4f-ca75-47d9-a1c3-68c97b42f166
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Coverage settings

[!include [banner](../includes/banner.md)]

Master scheduling uses coverage settings to calculate item requirements.

You can specify coverage settings in several ways:

- Specify coverage settings for a coverage group.

    You can create a coverage group that contains settings for all products that are linked to the coverage group. To create a coverage group, go to **Master planning &gt; Setup &gt; Coverage &gt; Coverage groups**. You can link a coverage group to a product. If the link is specific to a site, warehouse, or product dimension, use the **Coverage group** field on the **Item coverage** page. If the link is generic, regardless of the product dimensions, use the **Coverage group** field on the **Plan** FastTab of the **Product details** page. By default, if you don't link a coverage group to a product, master planning uses the general coverage group that is specified on the **Master planning parameters** page.

- Specify coverage settings for a product.

    You can create coverage settings for a specific product. Go to **Product information management &gt; Products &gt; Released products**. Select the product, and then, on the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage** to open the **Item coverage** page. If the product is already linked to a coverage group, you can override the coverage group settings by using the **Override** field. The coverage settings on the **Item coverage** page take precedence over the settings on the **Coverage group** page.

- Specify coverage settings for a product by using a wizard.

    The wizard guides you step by step through the process of setting up the primary item coverage parameters. On the **Item coverage** page, on the Action Pane, select **Wizard** to open the **Item Coverage Wizard**.

- Specify coverage settings for a dimension group.

    Go to **Product information management &gt; Products &gt; Released products**. On the **Released product details** page, on the **General** FastTab, in the **Administration** section, select the link in the **Storage dimension group** field. On the **Storage dimension groups** page, select the **Coverage plan by dimension** check box to create the coverage settings for a dimension in the storage dimension group. The **Coverage plan by dimension** field must be selected for all product dimensions, such as configuration, color, size, and style.


## Coverage codes

Master planning can be configured to use different replenishment methods. The replenishment methods or lot-sizing methods are the techniques used by the system to determine the batch size for purchased or produced items. 

Each replenishment method is assigned one of the following coverage codes:

- **Manual** - The lot-sizing method where the system does not suggest purchased, transfer, or production orders for the item. The planner for the item will be in charge of creating the required orders for the replenishment of the item.
- **Per requirement** - The lot-sizing method in which the system creates a planned purchase, transfer, or production order per requirement for the item. This is generally used for expensive items with intermittent demand.  
- **Per period** - The lot-sizing method that combines all the demand for a period into one order for the item. The order will be planned for the first day of the period and its quantity will fulfill the net requirements during the established period. The period starts with the first demand of the item and covers the defined length in time. The next period will start with the next requirements of the item.
- **Min/Max** - The lot-sizing method that contains the replenishment of inventory up to a certain level when the predicted on-hand is below a threshold. The replenishment quantity will be the difference between the maximum level and the predicted on-hand level.


## Additional resources

[Master plans overview](master-plans.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]