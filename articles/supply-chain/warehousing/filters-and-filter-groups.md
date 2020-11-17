---
# required metadata

title: Set up filters and filter groups
description: This topic describes how to set up filters and filter groups for filter codes. A filter is associated with a filter code and it can be used to categorize items in the item handling, purchase, and sales processes.
author: Mirzaab
manager: tfehr
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSFilters,WHSFilterGroupTable,EcoResProductDetailsExtended

audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-11-16
ms.dyn365.ops.version: Release 10.0.16
---

# Set up filters and filter groups

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This topic applies to features in the *Warehouse management* module. It does not apply to features in the Inventory management module.

This topic describes how to set up filters and filter groups for filter codes. A filter is associated with a filter code and it can be used to categorize items in the item handling, purchase, and sales processes. For example, for item handling you can use filters to make sure that heavy products are always located on the ground floor in a warehouse location. For purchase and sales processes, you can make specific items available for specific customers or vendors.

## Associate product filters with filter codes

A filter is always associated with a filter code. You can associate the filter with one or more filter codes when you create the filter. You can associate an unlimited number of filters with a filter code.

Product filters have been expanded to 10 **Filter title** characteristics (enum values) available to select when creating a product filter. The enum values *Code 1*, *Code 2* through *Code 10* are system defined to represent a given characteristic or attribute of an item.

For example, Code 1 could represent items that have hazardous material classification. Code 2 could represent items that can only be purchased by Vendors.  Product filters define the specific **Filter code** associated with the **Filter title**.

![Product filter codes](media/Product_Filters10.png "Product filter codes")

1. Go to **Warehouse management \> Setup \> Product filters \> Product filters**.
1. Select **New** in the **Action Pane** to create a new product filter.
1. Select an enum value from **Filter title**.
1. Enter a value in the **Filter code** field.
1. Enter a name for the code in the **Description** field.
    1. For example, *Code 2* represents vendors. You could create a product filter for a specific vendor, or a group of vendors. See "Setup vendor filter codes" below.

![Product filters](media/Product_Filters.png "Product filters")

## Set up product filter groups

You can use filter groups to filter codes. This is useful when the group is used in a query in a location directive and you want to search for the group instead of for a series of codes. A filter group is associated with an item group.

To set up filter groups, follow these steps:

1. Go to **Warehouse management \> Setup \> Product filters \> Product filter groups**.
1. Select **New** in the Action Pane.
1. In the **Group 1** and **Group 2** fields, enter the names that will be used to categorize items.
1. Select **New** in the **Details** FastTab to add a new line.
1. Enter the **Start date/time** and **End date/time** for the filter group.
1. Select the **Item group** to which the product filter will apply.
1. In the **Code 1**, **Code 2** through **Code 10** fields, select the filter codes to include in the group.

![Item group](media/ProdFilterGroup.png "Item group")

> [!NOTE]
> If you receive an error message when you close the form, a code setup may be missing. In the **Item groups** form, you can make the codes mandatory for an item group by selecting **Assign filter code 1 for item group**, **Assign filter code 2 for item group**, and so on.

## Next step

You can configure filters in different ways to make items available to specific vendors or customers, vendor groups or customer groups, and vendor accounts or customer accounts. By using filters, you can also make items generally available. When the filter setup of an item matches the information on an order, the item is allowed on the order.

After you have created filter codes and filter groups, you can configure the filters. For more information, see [Configure item filters and filter codes for warehouse transactions](filters-and-filter-codes.md).
