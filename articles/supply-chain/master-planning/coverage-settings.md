---
title: Coverage settings
description: Learn about the coverage settings that master scheduling uses to calculate item requirements, including an outline on coverage codes.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqGroup, ReqItemTable, ReqItemTableWizard, ReqItemTableSetup
ms.topic: how-to
ms.date: 03/24/2026
ms.custom: 
  - bap-template
---

# Coverage settings

[!include [banner](../includes/banner.md)]

Master scheduling uses coverage settings to calculate item requirements.

You can specify coverage settings in several ways:

- Specify coverage settings for a coverage group.

    Create a coverage group that contains settings for all products linked to the coverage group. To create a coverage group, go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**. You can link a coverage group to a product. If the link is specific to a site, warehouse, or product dimension, use the **Coverage group** field on the **Item coverage** page. If the link is generic, regardless of the product dimensions, use the **Coverage group** field on the **Plan** FastTab of the **Product details** page. By default, if you don't link a coverage group to a product, master planning uses the general coverage group that you specify on the **Master planning parameters** page.

- Specify coverage settings for a product.

    Create coverage settings for a specific product. Go to **Product information management** \> **Products** \> **Released products**. Select the product, and then, on the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage** to open the **Item coverage** page. If the product is already linked to a coverage group, you can override the coverage group settings by using the **Override** field. The coverage settings on the **Item coverage** page take precedence over the settings on the **Coverage group** page.

- Specify coverage settings for a product by using a wizard.

    The wizard guides you step by step through the process of setting up the primary item coverage parameters. On the **Item coverage** page, on the Action Pane, select **Wizard** to open the **Item Coverage Wizard**.

- Specify coverage settings for a dimension group.

    Go to **Product information management** \> **Products** \> **Released products**. On the **Released product details** page, on the **General** FastTab, in the **Administration** section, select the link in the **Storage dimension group** field. On the **Storage dimension groups** page, select the **Coverage plan by dimension** check box to create the coverage settings for a dimension in the storage dimension group. You must select the **Coverage plan by dimension** field for all product dimensions, such as configuration, color, size, and style.

## Coverage codes

You can configure master planning to use different replenishment methods. The system uses these replenishment methods, or lot-sizing methods, to determine the batch size for purchased or produced items.

Assign each replenishment method one of the following coverage codes:

- **Manual** – The lot-sizing method where the system doesn't suggest purchase, transfer, or production orders for the item. The planner for the item is responsible for creating the required orders to replenish the item.
- **Per requirement** – The lot-sizing method where the system creates a planned purchase, transfer, or production order for each requirement of the item. Use this method for expensive items with intermittent demand.  
- **Per period** – The lot-sizing method that combines all the demand for a period into one order for the item. The order is planned for the first day of the period, and its quantity fulfills the net requirements during the established period. The period starts with the first demand of the item and covers the defined length in time. The next period starts with the next requirements of the item.
- **Min/Max** – The lot-sizing method that replenishes inventory up to a certain level when the predicted on-hand quantity is below a threshold. The replenishment quantity is the difference between the maximum level and the predicted on-hand level.
- **Priority** – A strategy that replenishes buffers for a product according to its minimum, reorder point, and maximum stock quantities. Whenever the projected on-hand inventory falls below the reorder point quantity, the system replenishes it to its maximum quantity. For replenishing, priority (not date) is considered, which ensures that the most urgent orders are replenished first. Learn more in [Priority-based planning](planning-optimization/priority-based-planning.md).
- **Decoupling point** – The coverage code that identifies a product as a decoupling point (buffer) according to the Demand Driven Material Requirements Planning (DDMRP) methodology. DDMRP is a specific planning and execution methodology. To specify that a product is a decoupling point, open its **Item coverage** page and, under **Use specific settings**, set **Coverage code** to a coverage group that has coverage code of *Decoupling point*. For more information about the DDMRP methodology, see [Demand Driven Material Requirements Planning (DDMRP) overview](planning-optimization/ddmrp-overview.md).

## <a name="specify-versions-routes"></a>Demand-specified BOM or formula versions and routes

For make-to-order businesses, it can be useful to configure coverage groups to consider BOM or formula versions and routes specified in demand lines (such as sales order lines) when creating supply (such as planned production orders). For demand where no BOM or formula version or route is specified, the system chooses the currently active ones.

### Prerequisites

To use the **Prioritize existing supply over required BOM or formula version or route version** setting described in the next section, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature named *Prioritize existing supply over required BOM/route in Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.43, this feature is turned on by default.

The **Use the specified BOM or formula version** and **Use the specified route version** settings described in the next section don't require these prerequisites. However, without the *Prioritize existing supply over required BOM/route in Planning Optimization* feature, the system always works as though **Prioritize existing supply over required BOM or formula version or route version** is set to *No*.

### Configure a coverage group to use demand-specified BOM or formula versions and routes

To configure a coverage group to use the BOM or formula versions and routes specified in demand lines, follow these steps:

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. From the list pane, select the group you want to set up.
1. Make the following settings on the **General** FastTab for your selected group:
    - **Use the specified BOM or formula version** – Set to *Yes* to allow demand lines to identify a specific BOM or formula version when creating planned production orders for items that belong to the current coverage group. Set to *No* to always use the currently active BOM or formula version.
    - **Use the specified route version** – Set to *Yes* to allow demand lines to identify a specific route version when creating planned production orders for items that belong to the current coverage group. Set to *No* to always use the currently active route version.
    - **Prioritize existing supply over required BOM or formula version or route version** – This setting only applies when **Use the specified BOM or formula version** and/or **Use the specified route version** are set to *Yes*. Set this setting to *Yes* to prioritize existing supply (such as on-hand inventory, if available) over demand-specified BOM or formula versions and routes. Set to *No* if demand-specified BOM or formula versions or routes should always result in creating new supply (such as planned production orders), even if existing supply is available.

## Related information

- [Master plans overview](master-plans.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
