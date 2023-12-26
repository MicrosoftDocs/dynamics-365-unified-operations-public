---
title: Default order settings for dimensions and product variants
description: Default order settings in Dynamics 365 Supply Chain Management define the site and warehouse where items will be sourced from or stored; the minimum, maximum, multiple and standard quantities that will be used for trading or inventory management; the lead times; the stop flag; and the order promising method.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventItemOrderSetup, InventItemIdLookupByDefaultOrderSetting, EcoResProductReleasedStoppedAllChartPart, UnitTestPartitions
ms.topic: how-to
ms.date: 02/02/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Default order settings for dimensions and product variants

[!include [banner](../includes/banner.md)]

Default order settings in Dynamics 365 Supply Chain Management define the site and warehouse where items will be sourced from or stored; the minimum, maximum, multiple and standard quantities that will be used for trading or inventory management; the lead times; the stop flag; and the order promising method. Default order settings are used when creating purchase orders, sales orders, transfer orders, inventory journals, and by master planning for generating planned orders. Default order settings can be item specific, site specific, product variant specific, or product dimension specific.

To define the default order settings for a product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the relevant product in the grid.
1. On the Action Pane, follow one of these steps to open the **Default order settings** page for the selected product:

    - On the **Plan** tab, in the **Order settings** group, select **Default order settings**.
    - On the **Manage inventory** tab, in the **Order settings** group, select **Default order settings**.

1. Configure the settings as described in the rest of this article.

## Default order settings

There are three types of default order settings for purchases, sales, and inventory. The default order settings for purchases are used when creating:

- Purchase order lines
- Purchase agreement lines
- Request for quotation lines
- Purchase requisition lines
- Consignment replenishment lines (partially supported, see note)
- Planned purchase orders

> [!NOTE]
> For consignment replenishment order lines, the only settings from the **Purchase order** FastTab of the **Default order settings** page that apply are the **Default site** field, **Default warehouse** field, and **Stopped** check box.

The default order settings for sales are used when creating:

- Sales order lines
- Sales agreement lines
- Sales quotation lines
- Return order lines and item replacement lines
- Demand forecast lines

The default sales order settings also apply when creating:

- Project item requirements
- Service order item requirements

The default order settings for inventory are used when creating:

- Inventory journals
- Transfer orders
- Planned transfer orders

The default inventory order settings also apply when creating:

- Quarantine orders
- Quality orders
- Production orders
- BOM lines
- Planned production orders

## Full definition of a released product

When you create a transaction, you must specify the full definition of a released product on the line, so that Supply Chain Management can try to identify the default order settings. In the full definition of a released product, the item number and all the active product dimensions, such as configuration, size, style, version, and color, are specified on the transaction. For example, if you manually create a purchase order line for a released product variant, you must specify all the required product dimensions before the site, warehouse, quantities, and lead time will appear by default on the order line.

Not all of the default order settings parameters are applied when creating order or journal lines. Quantities and lead times will only display by default when appropriate. For example, when counting a journal line, only the site and warehouse will display by default when the line is created. For this reason, no default quantity or checks on multiple and minimums are performed when creating the line or posting the journal.

The system always attempts to find a default site and warehouse when an order or journal line is created. The site isn't always displayed by default from the order settings. For example, when creating a sales order or a purchase order, the site from the order header is automatically used on the order lines. When creating a BOM line, the site from the BOM header is used. After the site is determined, it will be used to find any site-specific order settings that can then be used as the default for the warehouse.

The default order type, the purchase, and the inventory lead times can be overridden by the item's coverage rules on the **Item coverage** page. Although the default order settings don't allow for the distinction between the production and transfer lead time, the item coverage rules allow for it. However, the item coverage setup will only be used by master planning when creating planned production and planned transfer orders and won't apply when manually creating production and transfer orders.

## Default order settings rules

You can define general default order settings and any number of default order setting rules that apply only in certain conditions, such as site or a specific product dimension or product dimensions combination. You can't define warehouse-specific order settings.

### Rank in default order settings

The default order settings rules have ranks. The higher the rank, the more important the rule is, meaning that it will have a higher priority and be used before the rules with lower ranks. The general default order settings have rank zero, which can't be modified. There can only be one rule with rank zero. Rules can have the same rank, provided that the dimensions they apply to differ. This is useful for modeling site-specific order settings. When a new default order settings rule is created, the values for order values, stop flag, etc. are inherited from the rule with rank zero, but can be overridden.

### Default order settings for released products

For distinct released products, you can define general order settings or site-specific order settings. The general order settings will always have rank zero. If you set up new sales, purchase, and inventory order settings at the same time, we recommend that you use the **Details view** on the **Default order settings** page. To switch to the details view, go to **Options \> Page options \> Change view \> Details view**.

### Site-specific order settings

To create site-specific order settings, select **New**. In **Details view**, enter the site in the **Site** field in the **Settings applicable for** section. In **Grid view**, enter the site in the **Site** column. The new rule is automatically assigned a new rank value that is more than 0 (zero). You can create as many site-specific rules as you require. To indicate that they're equally important, you can assign the same rank value to all the site-specific rules.

If you are in **Details view**, you can't get the overview of the rules created for the item. Use the **Show/Hide list** button to see overview information. When an order line of any type is created and it has no site provided, Supply Chain Management searches for a rule with no site specified. This helps to determine a default site on the order line. This site is then used to search for a site-specific rule, where a default warehouse may have been set. This warehouse is applied to the order line.

### Specific order settings for product dimension

You can define order settings rules for any active product dimension or combination of active product dimensions. If a product dimension field is empty, then that the rule applies to all values of the product dimension.

Consider the following example product.

| Item | Value |
|---|---|
| **Product name** | Photoelectric sensor |
| **Item number** | XW56 |
| **Configuration** (used to model the type of light) | C1-Visible red light, C2-Infrared light |
| **Version** | V1, V2, V3 |

For this example, assume that the product is procured and not produced. Also assume that configuration C1 is more commonly used, so it has shorter lead times.

Create the following default order settings to model this scenario.

| Rank | Site | Configuration | Version | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|---|---|---|---|---|---|---|---|---|
| 10 | | C1 | | Yes | 2 | | | |
| 0 | | | | | 5 | | | |

When a purchase order line or a planned purchase order is created for item XW56, configuration C1, regardless of the version or site where the line is put, the lead time will be considered 2. Assume that all versions besides V3 are stopped.

You can create the following default order settings rules.

| Rank | Site | Configuration | Version | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|---|---|---|---|---|---|---|---|---|
| 20 | | | V2 | Yes | | Yes | Yes | Yes |
| 20 | | | V1 | Yes | | Yes | Yes | Yes |
| 10 | | C1 | | Yes | 2 | | | |
| 0 | | | | | 5 | | | |

The two rules for stopping the old versions have the same rank. Therefore, they're equally important. Because both these rules have a higher rank than the rule for configuration C1, they take precedence over the rule for configuration C1.

This example explains the need for the rank. If the rank isn't used, when a purchase order is created for configuration C1 and version V2, the two rules that are defined for V2 and C1 will be ambiguous. To solve the ambiguity, Supply Chain Management will search through the rules in descending order of rank and apply the first applicable rule. In the current example, when a purchase order line is created for configuration C1 and version V2, the user will receive a warning message that states that the item is on hold, and that this hold is caused by the version value. If the rule for the configuration had a higher rank than the rule for the version, a purchase order line would be successfully created for configuration C1 and version V2, and the user would receive no "item on hold" message.

Consider the following default order setting rules.

| Rank | Site | Configuration | Version | Default site | Default warehouse | Purchase - Override default storage dimensions | Purchase warehouse |
|---|---|---|---|---|---|---|---|
| 20 | 2 | | | | | Yes | 22 |
| 10 | | C1 | V2 | 2 | 21 | | |
| 0 | | | | 1 | 11 | | |

The system traverses the set of rules two times to determine the site and warehouse. When a purchase order line is created for configuration C1, version V2, the site is determined based on the rule that has a rank of 10. The system then searches for a rule for site 2 to determine a warehouse. Rule 20 is found, and because it has a higher rank, the warehouse on the purchase order line will be 22, not 21.

As general guidance, specific rules and rules for dimensions that are more important than other dimensions get higher ranks, while more generic rules get lower ranks.

The rule with rank zero serves as a safety net. If no other rules are hit, then the default order settings from rule zero will be used.

Because the rank number is important, on the **Default order settings** Action Pane, there are functions to move a rule up or down and to renumber the rules, so that they're always in increments of 10.

The number of rules created for a released product may be many. In order to get a better understanding of what each rule is overriding and why it's needed, we recommend using the **Grid view** on the **Default order settings** page. You can enable the grid view by going to **Options \> Page options \> Change view \> Grid view**. The number of columns displayed in the grid could be significant, especially for the sales and inventory tabs. To limit the number of columns shown in the grid, groups of columns can be hidden or displayed by using the buttons on the **Default order settings \> Column display** menu.

### Specific order settings for released product variant

If the rule system for default order settings is too cumbersome, then there's the option to define default order settings for each product variant. The following example shows how this will look for the product and the cases described above.

| Rank | Site | Configuration | Version | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|---|---|---|---|---|---|---|---|---|
| 10 | | C2 | V3 | Yes | 5 | | | |
| 10 | | C2 | V2 | Yes | 5 | Yes | Yes | Yes |
| 10 | | C2 | V1 | Yes | 5 | Yes | Yes | Yes |
| 10 | | C1 | V3 | Yes | 2 | | | |
| 10 | | C1 | V2 | Yes | 2 | Yes | Yes | Yes |
| 10 | | C1 | V1 | Yes | 2 | Yes | Yes | Yes |
| 0 | | | | | 5 | | | |

The rank in this case doesn't really matter, so you can choose to hide it. This solution potentially introduces a maintenance issue. However, you may want to consider using this setup if you're considering integrating with Product Lifecycle Management (PLM) systems.

## Use strict or standard validation of default order quantities

You can choose how strict the system should be when validating quantities entered in the **Default order settings** for a product. When you use the new strict option, the **Standard order quantity** must always be a multiple of the specified **Multiple** value for purchase orders, inventory, and sales orders. If you're using strict validation, you won't be able to save default order settings that don't meet this requirement (and an error is shown in the message bar).

Strict validation applies to **Standard order quantity** values specified on the **Purchase order**, **Inventory**, and **Sales order** FastTabs of the **Default order settings** page. Each FastTab has its own **Multiple** setting, which is used to validate the **Standard order quantity** value specified for that FastTab.

### Turn the strict validation option on or off

To use strict validation, the *Strict validation on default order quantities* feature must be turned on for your system. As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then you can turn this functionality on or off by going to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and searching for the *Strict validation on default order quantities* feature.

### Set the validation option

To set the validation option:

1. Go to **Product information management \> Setup \> Product information management parameters**.
1. On the **General** tab, set **Validation on default order quantities** to one of the following values:
    - **Strict** - Select this option to ensure that all **Standard order quantity** values will be a multiple of the **Multiple** value for each FastTab (**Purchase order**, **Inventory**, and **Sales order**).
    - **Standard** - Select this option to use standard validation (which works the same as when this feature isn't enabled).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
