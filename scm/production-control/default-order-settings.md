---
# required metadata

title: Default order settings for dimensions and product variants
description: Default order settings define the site and warehouse where items will be sourced from or stored, the minimum, maximum, multiple and standard quantities that will be used for trading or inventory management, the lead times, the stop flag, and the order promising method. Default order settings are used when creating purchase orders, sales orders, transfer orders, inventory journals, and by master planning for generating planned orders. Default order settings can be item specific, site specific, product variant specific, or product dimension specific.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-11-01 12 - 13 - 21
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventItemOrderSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 223084
ms.assetid: fbfbcd7b-dc75-44ab-bffc-8bad576804a4
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Default order settings for dimensions and product variants

Default order settings define the site and warehouse where items will be sourced from or stored, the minimum, maximum, multiple and standard quantities that will be used for trading or inventory management, the lead times, the stop flag, and the order promising method. Default order settings are used when creating purchase orders, sales orders, transfer orders, inventory journals, and by master planning for generating planned orders. Default order settings can be item specific, site specific, product variant specific, or product dimension specific.

You can define the default order settings on the **Default order settings** page. To open this page, go to **Product information management** &gt; **Products** &gt; **Released products** &gt; select a released product &gt; on the **Plan** or ****Manage inventory**** Action Pane &gt; **Order settings** &gt; **Default order settings**.

## Default order settings
There are three types of default order settings for purchases, sales, and inventory. The default order settings for purchases are used when creating:

-   Purchase order lines
-   Purchase agreement lines
-   Request for quotation lines
-   Purchase requisition lines
-   Consignment replenishment lines
-   Planned purchase orders

The default order settings for sales are used when creating:

-   Sales order lines
-   Sales agreement lines
-   Sales quotation lines
-   Return order lines and item replacement lines
-   Demand forecast lines

The  default sales order settings also apply when creating:

-   Project item requirements
-   Service order item requirements

The default order settings for inventory are used when creating:

-   Inventory journals
-   Transfer orders
-   Planned transfer orders

The  default inventory order settings also apply when creating:

-   Quarantine orders
-   Quality orders
-   Production orders
-   BOM lines
-   Planned production orders

## Full definition of a released product
When creating a transaction, you need to specify the full definition of a released product on the line before Dynamics 365 for Operations attempts to identify the default order settings. The full definition of released product means that the item number and all the active product dimensions, such as configuration, size, style, and color, are specified on the transaction. For example, if you manually create a purchase order line for a released product variant, you need to specify all of the required product dimensions before the site, warehouse, quantities, and lead time will display by default on the order line. 

Not all of the default order settings parameters are applied when creating order or journal lines. Quantities and lead times will only display by default when appropriate. For example, when counting a journal line, only the site and warehouse will display by default when the line is created. Obviously no quantity defaulting or checks on multiple and minimums are performed when creating the line or posting the journal. 

The system always attempts to find a default site and warehouse when a order or journal line is created. The site is not always displayed by default from the order settings. For example, when creating a sales order or a purchase order, the site from the order header is automatically used on the order lines. When creating a BOM line, the site from the BOM header is used. After the site is determined, it will be used to find any site specific order settings that can then be used as the default for the warehouse. 

The default order type, the purchase, and the inventory lead times can be overriden by the item's coverage rules on the **Item coverage** page. Although the default order settings don't allow for the distinction between the production and transfer lead time, the item coverage rules allow for it. However, the item coverage setup will only be used by MRP when creating planned production and planned transfer orders and will not apply when manually creating production and transfer orders. 

## Default order settings rules
You can define general default order settings and any number of default order setting rules that apply only in certain conditions, such as site or a specific product dimension or product dimensions combination. You can't define warehouse specific order settings.

### Rank in default order settings

The default order settings rules have ranks. The higher the rank, the more important the rule is, meaning that it will have a higher priority and be used before the rules with lower ranks. The general default order settings have rank zero, which can't be modified. There can only be one rule with rank zero. Rules can have the same rank, provided that the dimensions they apply to differ. This is useful for modelling site specific order settings. When a new default order settings rule is created, the values for order values, stop flag, etc. are inherited from the rule with rank zero, but can be overriden.

### Default order settings for released products

For distinct released products, you can define general order settings or site specific order settings. The general order settings will always have rank zero. If you set up new sales, purchase and inventory order settings together at the same time, we recommend that you use the **Details view** on the **Default order settings** page. To switch to the details view, go to the **Options** Action Pane &gt; **Page options** &gt; **Change view** &gt; **Details view**.

### Site specific order settings

To create site specific order settings, click **New**. In **Details view**, fill in the site in the **Settings applicable for** &gt; **Site** field. In the **Grid view**, fill in the site in the **Site** column. The new rule will automatically get a new rank value, higher than zero. You can create as many site specific rule as needed and you can assign all the site specific rules the same rank, to model that they are equally important. 

If you are in **Details view**, you can't get the overview of the rules created for the item. Toggle the **Show/Hide list** button to see overview information. When an order line of any type is created and it has no site provided, Dynamics 365 for Operations searches for a rule with no site specified. This could help determine a default site on the order line. This site is then used to search for a site specific rule, where a default warehouse may have been set. This warehouse is applied to the order line.

### Specific order settings for product dimension

You can define order settings rules for any active product dimension or combination of active product dimensions. If a product dimension field is left empty, then that the rule applies to all values of the product dimension. 

Consider the following example product.

|                                                     |                                         |
|-----------------------------------------------------|-----------------------------------------|
| **Product name**                                    | Photoelectric sensor                    |
| **Item number**                                     | XW56                                    |
| **Configuration** (used to model the type of light) | C1-Visible red light, C2-Infrared light |
| **Style** (used to model the engineering revision)  | R1, R2, R3                              |

For this example, assume that the product is procured and not produced. Also assume that configuration C1 is more commonly used, so it has shorter lead times. 

Create the following default order settings to model this scenario.

| Rank | Site | Configuration | Style | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|------|------|---------------|-------|--------------------------------------|--------------------|--------------------|-----------------------------------|-----------------|
| 10   |      | C1            |       | Yes                                  | 2                  |                    |                                   |                 |
| 0    |      |               |       |                                      | 5                  |                    |                                   |                 |

When a purchase order line or a planned purchase order is created for XW56, Configuration C1, regardless of the revision or site the line is placed at, the lead time will be considered 2. Assume that all revisions besides R3 are stopped.

You can create the following default order settings rules.

| Rank | Site | Configuration | Style | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|------|------|---------------|-------|--------------------------------------|--------------------|--------------------|-----------------------------------|-----------------|
| 20   |      |               | R2    | Yes                                  |                    | Yes                | Yes                               | Yes             |
| 20   |      |               | R1    | Yes                                  |                    | Yes                | Yes                               | Yes             |
| 10   |      | C1            |       | Yes                                  | 2                  |                    |                                   |                 |
| 0    |      |               |       |                                      | 5                  |                    |                                   |                 |

The two rules for stopping the old revisions have the same ranking, meaning they are equally important. Both of them have a higher rank than the rule for configuration C1, meaning that they take precedence over the rule for configuration C1. 

This example explains the need for the rank. If a purchase order is created for configuration C1 and revision R2, in the absence of the rank, the two rules defined for R2 and C1 would be ambiguous. To solve the ambiguity, Dynamics 365 for Operations will search through the rules in descending order of rank and apply the first applicable rule. In the current example, when a purchase order line is created for configuration C1 and revision R2, the user will get a warning message that the item is on hold and that this is caused by the revision value. If the rule for the configuration had a higher rank than the one for revision, then the creation of a purchase order line for configuration C1 and revision R2 would have succeeded and no 'item on hold' message would have be given to the user. 

Consider the following default order setting rules.

| Rank | Site | Configuration | Style | Default site | Default warehouse | Purchase - Override default storage dimensions | Purchase warehouse |
|------|------|---------------|-------|--------------|-------------------|------------------------------------------------|--------------------|
| 20   | 2    |               |       |              |                   | Yes                                            | 22                 |
| 10   |      | C1            |  R2   |  2           |  21               |                                                |                    |
| 0    |      |               |       | 1            | 11                |                                                |                    |

The system traverses the set of rules two times in order to determine the site and warehouse. When a purchase order line is created for configuration C1, style R2, the site is determined based on the rule with rank 10. Then the system searches for a rule for site 2 in order to determine a warehouse. Rule 20 is found and because it has a higher rank, the warehouse on the purchase order line will be 22, and not 21. 

As a general guidance, specific rules and rules for dimensions that are more important than other dimensions get higher ranks, while more generic rules get lower ranks. 

The rule with rank zero serves as a safety net. If no other rules are hit, then the default order settings from rule zero will be used. 

Because the rank number is so important, on the **Default order settings** Action Pane, there are functions to move a rule up or down and to renumber the rules, so that they are always in increments of 10. 

The number of rules created for a released product may be many. In order to get a better sense of what each rule is overriding and why it's needed, we recommend using the **Grid view** on the **Default order settings** page. You can enable the grid view by going to the **Options** Action Pane &gt; **Page options** &gt; **Change view** &gt; **Grid view**. The number of columns displayed in the grid could be quite significant, especially for the sales and inventory tabs. To limit the number of columns shown in the grid, groups of columns can be hidden or displayed by using the buttons on the **Default order settings** &gt; **Column display** menu.

### Specific order settings for released product variant

If the rule system for default order settings is too cumbersome, then there is the option of simply defining default order settings for each product variant. The following examples shows how this will look for the product and the cases described above.

| Rank | Site | Configuration | Style | Purchase - Override default settings | Purchase lead time | Purchase - Stopped | Sales - Override default settings | Sales - Stopped |
|------|------|---------------|-------|--------------------------------------|--------------------|--------------------|-----------------------------------|-----------------|
| 10   |      | C2            | R3    | Yes                                  | 5                  |                    |                                   |                 |
| 10   |      | C2            | R2    | Yes                                  | 5                  | Yes                | Yes                               | Yes             |
| 10   |      | C2            | R1    | Yes                                  | 5                  | Yes                | Yes                               | Yes             |
| 10   |      | C1            | R3    | Yes                                  | 2                  |                    |                                   |                 |
| 10   |      | C1            | R2    | Yes                                  | 2                  | Yes                | Yes                               | Yes             |
| 10   |      | C1            | R1    | Yes                                  | 2                  | Yes                | Yes                               | Yes             |
| 0    |      |               |       |                                      | 5                  |                    |                                   |                 |

The rank in this case doesn't really matter, so you can choose to hide it. This solution potentially introduces a maintenance issue. However, you may want to consider using this setup if you are consider integrating with Product Lifecycle Management (PLM) systems.

