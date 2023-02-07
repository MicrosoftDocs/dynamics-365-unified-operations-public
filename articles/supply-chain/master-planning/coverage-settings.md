---
title: Coverage settings
description: This article provides information about the coverage settings that master scheduling uses to calculate item requirements.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: ReqGroup, ReqItemTable, ReqItemTableWizard, ReqItemTableSetup
ms.topic: how-to
ms.date: 01/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
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

- **Manual** – The lot-sizing method where the system doesn't suggest purchased, transfer, or production orders for the item. The planner for the item will be in charge of creating the required orders for the replenishment of the item.
- **Per requirement** – The lot-sizing method in which the system creates a planned purchase, transfer, or production order per requirement for the item. This is generally used for expensive items with intermittent demand.  
- **Per period** – The lot-sizing method that combines all the demand for a period into one order for the item. The order will be planned for the first day of the period and its quantity will fulfill the net requirements during the established period. The period starts with the first demand of the item and covers the defined length in time. The next period will start with the next requirements of the item.
- **Min/Max** – The lot-sizing method that contains the replenishment of inventory up to a certain level when the predicted on-hand is below a threshold. The replenishment quantity will be the difference between the maximum level and the predicted on-hand level.
- **Priority** – A strategy that allows you to replenish buffers for a product according to its minimum, reorder point, and maximum stock quantities. Whenever the projected on-hand inventory falls below the reorder point quantity, it will be replenished to its maximum quantity. For replenishing, priority (not date) is considered, which ensures that the most urgent orders are replenished first. For more information, see [Priority-based planning](planning-optimization/priority-based-planning.md).
- **Decoupling point** – The coverage code that identifies a product as a decoupling point (buffer) according to the Demand Driven Material Requirements Planning (DDMRP) methodology. DDMRP is a specific planning and execution methodology. To specify that a product is a decoupling point, open its **Item coverage** page and, under **Use specific settings**, set **Coverage code** to a coverage group that has coverage code of *Decoupling point*. For more information about the DDMRP methodology, see [Demand Driven Material Requirements Planning (DDMRP) overview](planning-optimization/ddmrp-overview.md).

## Additional resources

- [Master plans overview](master-plans.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
