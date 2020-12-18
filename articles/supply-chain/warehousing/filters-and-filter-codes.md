---
# required metadata

title: Configure product filters for warehouse transactions
description: This topic describes how to configure product filters and filter codes to categorize inventory items in a warehouse. You can also use filters to specify which customers can order a particular item and specify the items that can be purchased from a particular vendor.
author: Mirzaab
manager: tfehr
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSFilters,WHSFilterGroupTable,EcoResProductDetailsExtended,WHSFilterGenerallyAvail
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

# Configure product filters for warehouse transactions

[!include [banner](../includes/banner.md)]

This topic describes how to configure product filters and filter codes to categorize inventory items in a warehouse. You can also use filters to specify which customers can order a particular item and specify the items that can be purchased from a particular vendor.

Additionally, you can set up and use product filters to automatically organize inventory items in a warehouse and combine filtered items into filter groups. Filters can be used to place items into categories for handling, purchasing and selling processes. You may want to group items together or separate them from each other when handling based on weight or handling restrictions. You can also specify which customers or vendors an item can be purchase from or sold to.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Prerequisite | Instructions  |
| -- | -- |
| Before you start configuring products on the **Released product details** page, you must enable the Warehouse processing for the product’s *storage dimension group*. | Go to **Product information management \> Setup \> Dimension and variant groups \> Storage dimension groups** and select or create a storage dimension group where the **Use warehouse management processes** check box is set to *Yes*. |
| If you will be using customer or vendor filters, you must first enable their use in **Warehouse management parameters**. | Go to **Warehouse management \> Setup \> Warehouse management parameters**. Open the **Product filters** tab, then enable the customer and or vendor filters by setting the toggle to *Yes*. |

![Enable Customer-Vendor filter](media/ProdFilterCusVenFilter.png "Enable Customer-Vendor filter")

## Set up product filters

Product filters provide up to 10 **Filter title** characteristics (enum values), which are available to select when creating a product filter. The enum values *Code 1*, *Code 2* through *Code 10* are system defined to represent a given characteristic or attribute of an item.

For example, Code 1 could represent items that have hazardous material classification. Code 2 could represent items that can only be purchased by vendors. Product filters define the specific **Filter code** associated with the **Filter title**.

1. Go to **Warehouse management \> Setup \> Product filters \> Product filters**.
1. Select **New** on the Action Pane to create a new product filter to the grid.
    ![Product filter codes](media/Product_Filters10.png "Product filter codes")
1. Select a value in the **Filter title** column.
1. Enter a value in the **Filter code** column.
1. Enter a name for the code in the **Description** field. For example, *Code 2* could represents vendors. You could then create a product filter for a specific vendor, or a group of vendors. See [Setup vendor filter codes](#vendor-product-filters) later in this topic.

    ![Product filters](media/Product_Filters.png "Product filters")

## Set up product filter groups

You can use filter groups to filter codes. This is useful when a group is used in a query in a location directive and you want to search for the group instead of for a series of codes. Each filter group is associated with an item group.

> [!IMPORTANT]
> Not all product filter groups are enabled for filter codes higher than *Code 4* (that is, *Code 5* through *Code 10*). For instance, on released products, all of the product filter codes will be added, but the grouping of filter codes will not be updated. This behavior may be updated in later releases.

To set up filter groups, follow these steps:

1. Go to **Warehouse management \> Setup \> Product filters \> Product filter groups**.
1. Select **New** on the Action Pane.
1. In the **Group 1** and **Group 2** fields, enter the names that will be used to categorize items.
1. Select **New** on the **Details** FastTab toolbar to add a new line.
1. Enter the **Start date/time** and **End date/time** for the filter group.
1. Select the **Item group** to which the product filter will apply.
1. In the **Code 1**, **Code 2** through **Code 10** fields, select the filter codes to include in the group, as needed.

    ![Item group](media/ProdFilterGroup.png "Item group")

> [!NOTE]
> If you receive an error message when you close the page, a code setup may be missing. On the **Item groups** page, you can make the codes mandatory for an item group by selecting **Assign filter code 1 for item group**, **Assign filter code 2 for item group**, and so on.

## Set up filter codes on item groups

By setting up filter codes on an item group, you can make the codes required for products attached to the item group.

To set up filter codes on item groups, follow these steps:

1. Select **Inventory management \> Setup \> Inventory \> Item groups**.
1. Select **New** on the Action Pane to create a new item group. Enter a value in **Item group** and the description in **Name**.
1. On the **Warehouse** FastTab, in the **Filter required** group, select the appropriate check boxes to define one or more filter codes that must be specified for products that are associated with the item group.

    To update a released product, open its **Released product details** page and, on the Action Pane, select **Edit**. The filters associated with codes then become available on the **Warehouse** FastTab.

    ![Item groups](media/ItemGroup10.png "Item groups")

1. In the **Item group filter** section, select the appropriate check boxes to define which filters must match for the filter group to be the default for an item.

    For example, if **Use filter code 1** and **Use filter code 2** are selected, then both **Filter code 1** and **Filter code 2** of the item must match the setup of the filter group for the item group before the filter group can be selected. When you create a new item, the selected filter group will be the default in the **Released product details** page, on the **Warehouse** FastTab, in the **Group 1** and **Group 2** fields.


> [!IMPORTANT]
> Product filter codes are only enabled for items using advanced warehouse management.

## Specify filter codes for released products

Follow these steps to specify filter codes for released products. For example, you can use filter codes to group products that are hazardous and purchased by specific vendors.

To specify filter codes for specific products, follow these steps:

1. Select **Product information management** \> **Products** \> **Released products**.
1. On the **Action Pane** select **New** to create a new product.
1. On the **New released product** dialog box, enter the data needed to create the base of a new product, then select **OK**.

    - Product filter codes are not enabled unless the item group attached to the product has been configured for filter codes.
    - For more information, see [Create a new product](../pim/tasks/create-new-product.md).

1. Expand the **Warehouse** FastTab.
1. In the **Product filter codes** group, select filter codes for the **Code 1** through **Code 10** fields as needed to specify filter codes for the product.

## Set up generally available items

You can make specific inventory items available only for customers, only for vendors, or for both customers and vendors.

> [!NOTE]
> Customer and vendor filters don't apply for any item set up as generally available.

To set up generally available items, follow these steps:

1. Select **Warehouse management** \> **Setup** \> **Product filters** \> **Generally available products**.

1. On the Action Pane, select **New** to create a new record.
1. In the **Customer or vendor** field, select *Customer*, *Vendor*, or *All* to make the items available for customers, vendors, or both.
1. In the **Start date/time** field, enter the first date and time that the item will be available.
1. In the **Item group** field, select an item group.
1. In the **Code 1** through **Code 10** fields, select the filter codes to limit the items that are generally available.

    - When you select an item group, you set this group of items to be generally available.
    - By selecting filter codes in these fields, you limit the items that are available.

## Set up customer product filters

This optional procedure shows how to specify items that should be available for a customer in addition to the items that are made available via the filter setup on the **Generally available items** page. You can set up multiple filters for a single customer.

To set up customer filter codes, follow these steps:

1. Select **Sales and marketing \> Customers \> All customers**.
1. Select a customer.
1. On the Action Pane, open the **Customer** tab and, in the **Set up** group, select **Product filters**.
1. The **Product filter codes** page opens. Select **New** on the Action Pane.
1. In the **Start date/time** and **End date/time** fields, enter a start and end date for the selected item group.
1. In the **Item group** field, select an item group.
1. In the **Code 1** through **Code 10** fields, select codes to use as criteria for limiting the items that are available for customers in the selected item group. You must make a selection for each filter code set up for the item group.

## <a name="vendor-product-filters"></a>Set up vendor product filters

This optional procedure shows how to specify items that should be available for a vendor in addition to the items that are made available via the filter setup on the **Generally available items** page. You can set up multiple filters for a single vendor.

To set up vendor filter codes, follow these steps:

1. Select **Procurement and sourcing \> Vendors \> All vendors**.
1. Select a vendor.
1. On the Action Pane, open the **Vendor** tab and, in the **Set up** group, select **Product filters**.
1. The **Filter codes** page opens. Select **New** on the Action Pane.
1. In the **Start date/time** and **End date/time** fields, enter a start and end date for the selected item group.
1. In the **Item group** field, select an item group.
1. In the **Code 1** through **Code 10** fields, select codes to use as criteria for limiting the items that are available for vendors in the selected item group. You must make a selection for each filter code set up for the item group.

> [!NOTE]
> The enabling of vendor filters applies to released products where the associated storage dimension group has warehouse management processes enabled. The filter codes are used to determine whether the system will permit users to purchase a given item from a given vendor while creating purchase order lines. Supply Chain Management has two different methods to handle vendor approval. If one or more released products exist where the **Approved vendor check method** is *Warning only* or *Not allowed*, you risk enabling two vendor approval methods for those items. This may cause issues when creating purchase order lines.

## See also

[Set up filters and filter groups](filters-and-filter-groups.md)

[For more information see the blog post WMS-Warehouse Filter Codes](http://blog.dynamics-for-operations.com/2017/09/26/wms-warehouse-filter-codes/)
