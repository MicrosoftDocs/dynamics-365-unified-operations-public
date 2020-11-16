---
# required metadata

title: Configure item filters and filter codes for warehouse transactions
description: This topic describes how to configure item filters and filter codes to categorize inventory items in a warehouse. You can also use filters to specify which customers can order a particular item and specify the items that can be purchased from a particular vendor.
author: Mirzaab
manager: tfehr
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
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

# Configure item filters and filter codes for warehouse transactions

[!include [banner](../includes/banner.md)]

This topic describes how to configure item filters and filter codes to categorize inventory items in a warehouse. You can also use filters to specify which customers can order a particular item and specify the items that can be purchased from a particular vendor.

Additionally, you can set up and use filter codes to automatically organize inventory items in a warehouse and combine filtered items into filter groups.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Prerequisite</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Before you start configuring products in the <strong>Released product details</strong> form, you must enable the Warehouse processing for the product’s storage dimension group.</p></td>
<td><ol>
<li><p>Click <strong>Product information management</strong> &gt; <strong>Setup</strong> &gt; <strong>Dimension groups</strong> &gt; <strong>Storage dimension groups</strong>.</p></li>
<li><p>Select a storage dimension group, and then select the <strong>Use warehouse management processes</strong> check box.</p></li>
</ol>
<p></p></td>
</tr>
</tbody>
</table>


## Set up filter codes on item groups

By setting up filter codes on an item group, you can make the codes required for products in the item group.

To set up filter codes on item groups, follow these steps:

1.  Click **Inventory management** \> **Setup** \> **Inventory** \> **Item groups**.

2.  Click **New** to create a new item group. Enter the required details for the item group. For more information, see [Item group (form)](https://technet.microsoft.com/library/aa575515\(v=ax.60\)).

3.  On the **Warehouse management** FastTab, under **Filter required**, select the appropriate check boxes to define one or more filter codes that must be specified for products that are associated with the item group. To update a product, in the **Released product details** form, on the **Action Pane**, in the **Maintain** group, click **Edit**. The filters associated with a code become available on the **Warehouse management** tab.

4.  Under **Item group filter**, select the appropriate check boxes to define which filters must match for the filter group to be the default for an item. For example, if code 1 and code 2 are selected, then both filter code 1 and 2 of the item must match the setup of the filter group for the item group before the filter group can be selected. When you create a new item, the selected filter group will be the default in the **Released product details** form, on the **Warehouse management** FastTab, in the **Group 1** and **Group 2** fields.

## Specify filter codes for released products

Follow these steps to specify filter codes for released products. For example, you can use filter codes to group products that must be located in a storage zone with a specific temperature.

To specify filter codes for specific products, follow these steps:

1.  Click **Product information management** \> **Common** \> **Released products**.

2.  On the **Action Pane**, in the **New** group, click **Product** to create a new product. For more information, see [Key tasks: Define products](key-tasks-define-products.md).

3.  Click **Edit**, and then expand the **Warehouse management** FastTab.

4.  In the **Code 1**, **Code 2**, **Code 3**, and **Code 4** fields, select the filter codes that you want to specify for the product.

## Set up generally available items

You can make specific inventory items available only for customers or vendors, or for both customers and vendors. For any item that you set up as generally available, customer filters and vendor filters do not apply.

To set up generally available items, follow these steps:

1.  Click **Warehouse management** \> **Setup** \> **Filters** \> **Generally available items**.

2.  Click **New** to create a new record.

3.  In the **Customer or vendor** field, select **Customer**, **Vendor**, or **All** to make the items available for customers, vendors, or both.

4.  In the **Start date/time** field, enter the start date and the start time for the item’s availability.

5.  In the **Item group** field, select an item group.

6.  In the **Code 1**, **Code 2**, **Code 3**, and **Code 4** fields, select filter codes to limit the items that are generally available. When you select an item group, you set this group of items to be generally available. By selecting filter codes in these fields, you limit the items that are available.

## Optional: Set up customer filter codes

This procedure shows how to specify items that should be available for a customer in addition to the items that are made available via the filter setup in the **Generally available items** form. You can set up multiple filters for a single customer.

To set up customer filter codes, follow these steps:

1.  Click **Accounts receivable** \> **Common** \> **Customers** \> **All customers**.

2.  Select a customer.

3.  On the **Customer** tab, in the **Set up** group, click **Filters**.

4.  In the **Filter codes** form, click **New**.

5.  In the **Start date/time** and **End date/time** fields, enter the information for the selected customer.

6.  In the **Item group** field, select an item group.

7.  In the **Code 1**, **Code 2**, **Code 3**, and **Code 4** fields, select codes to use as criteria for limiting the items that are available for customers in the selected item group.

## Optional: Set up vendor filter codes

This procedure shows how to specify items that should be available for a vendor in addition to the items that are made available via the filter setup in the **Generally available items** form. You can set up multiple filters for a single vendor.

To set up vendor filter codes, follow these steps:

1.  Click **Accounts payable** \> **Common** \> **Vendors** \> **All vendors**.

2.  Select a vendor.

3.  On the **Vendor** tab, in the **Set up** group, click **Filters**.

4.  In the **Filter codes** form, click **New**.

5.  In the **Start date/time** and **End date/time** fields, enter the information for the selected vendor.

6.  In the **Item group** field, select an item group.

7.  In the **Code 1**, **Code 2**, **Code 3**, and **Code 4** fields, select codes to use as criteria for limiting the items that are available for vendors in the selected item group.

## See also

[Set up filters and filter groups](filters-and-filter-groups.md)

