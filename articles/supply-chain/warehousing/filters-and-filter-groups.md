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

# Set up filters and filter groups

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This topic applies to features in the *Warehouse management* module. It does not apply to features in the Inventory management module.

This topic describes how to set up filters and filter groups for filter codes. A filter is associated with a filter code and it can be used to categorize items in the item handling, purchase, and sales processes. For example, for item handling you can use filters to make sure that heavy products are always located on the ground floor in a warehouse location. For purchase and sales processes, you can make specific items available for specific customers or vendors.

## Associate filters with filter codes

A filter is always associated with a filter code. You can associate the filter with one or more filter codes when you create the filter. You can associate an unlimited number of filters with a filter code.

To associate filters with filter codes, follow these steps:

1.  Click **Warehouse management** \> **Setup** \> **Filters** \> **Filters**.

2.  Click **New**. In the **Filter title** field, select **Code 1**.

3.  In the **Filter code** field, enter a name for the filter.

4.  Optional: Repeat steps 2 and 3. Select **Code 2**, **Code 3**, and **Code 4** for additional filters that you want to create.

## Set up filter groups

You can use filter groups to filter codes. This is useful when the group is used in a query in a location directive and you want to search for the group instead of for a series of codes. A filter group is associated with an item group.

To set up filter groups, follow these steps:

1.  Click **Warehouse management** \> **Setup** \> **Filters** \> **Filter groups**.

2.  Click **New**. In the **Group 1** and **Group 2** fields, enter the names that will be used to categorize items.

3.  Select the start date and end date for the filter group.

4.  In the **Code 1**, **Code 2**, **Code 3**, and **Code 4** fields, select the filter codes to include in the group.
    

    > [!NOTE]
    > <P>If you receive an error message when you close the form, a code setup may be missing. In the <STRONG>Item groups</STRONG> form, you can make the codes mandatory for an item group by selecting <STRONG>Assign filter code 1 for item group</STRONG>, <STRONG>Assign filter code 2 for item group</STRONG>, and so on.</P>

    
    For more information, see [Configure item filters and filter codes for warehouse transactions](filters-and-filter-codes.md).

## Next step

You can configure filters in different ways to make items available to specific vendors or customers, vendor groups or customer groups, and vendor accounts or customer accounts. By using filters, you can also make items generally available. When the filter setup of an item matches the information on an order, the item is allowed on the order.

After you have created filter codes and filter groups, you can configure the filters. For more information, see [Configure item filters and filter codes for warehouse transactions](filters-and-filter-codes.md).