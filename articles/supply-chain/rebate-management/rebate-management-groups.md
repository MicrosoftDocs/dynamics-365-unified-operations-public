---
# required metadata

title: Rebate management groups
description: This topic describes how to set up Rebate management groups, which can be used during rebate calculations and attached to a master record.
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateGroup
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management groups

[!include [banner](../includes/banner.md)]

Rebate and deduction calculations can be driven by groups. A group can be attached to a master record. Rebate management groups can be created for customers, vendors and items.

## Rebate management customer groups

The calculation for a group of customers is often created for a chain of companies, such as a supermarket chain or franchise company. This type of calculation normally relates to a rebate.

A deduction is often calculated irrespective of whom it was sold to. However, there are exceptions, for example a licensee may construct a deductions scheme whereby customer group A will receive 4% and for customer group B they only receive 3%.

### Set up customer groups

To work with rebate management customer groups, go to **Rebate management \> Rebate management groups setup \> Customer groups**. Use commands on the Action Pane to add and remove groups as needed. For each group, make the following settings:

- **Rebate management group** - Enter a unique name for the group.
- **Description** - Enter a description of the group to provide more information about how it should be used.

### Manage customer group assignments

Each customer can belong to any number of rebate management groups. You can view and assign group members starting either from the groups list or from the customers list.

To view, add, or remove customers for a selected group:

1. Go to **Rebate management \> Rebate management groups setup \> Customer groups**.
1. Select the group you want to manage.
1. From the Action Pane, select **Customers**. The **Rebate management groups** page opens, showing a list of customers that are already members of the selected group.
1. To add a new customer to the group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Customer account** - Select the customer account ID.
    - **Name** - Enter a name and/or description of the customer.
1. To remove a customer from the group, select the customer and select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected customer:

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer you want to work with.
1. On the Action Pane, open the **Customer** tab and, from the **Rebate management** group, select **Rebate management groups**.
1. The **Rebate management groups** page opens, showing a list of groups that the selected customer already belongs to.
1. To add the customer to a new group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Rebate management group** - Select the group you want to add.
    - **Description** - Enter a description of the group, for example to explain why this customer is a member of it.
1. To remove a customer from a group, select the group and then select **Delete** on the Action Pane.

## Rebate management vendor groups

The calculation for a group of vendors is often created for a group of delivery points. This type of calculation normally relates to a rebate.

### Set up vendor groups

To work with rebate management vendor groups, go to **Rebate management \> Rebate management groups setup \> Vendor groups**. Use commands on the Action Pane to add and remove groups as needed. For each group, make the following settings:

- **Rebate management group** - Enter a unique name for the group.
- **Description** - Enter a description of the group to provide more information about how it should be used.

### Manage vendor group assignments

Each vendor can belong to any number of rebate management groups. You can view and assign group members starting either from the groups list or from the vendor list.

To view, add, or remove vendors for a selected group:

1. Go to **Rebate management \> Rebate management groups setup \> Vendor groups**.
1. Select the group you want to manage.
1. From the Action Pane, select **Vendors**. The **Rebate management groups** page opens, showing a list of vendors that are already members of the selected group.
1. To add a new vendor to the group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Vendor account** - Select the vendor account ID.
    - **Name** - Enter a name and/or description of the vendor.
1. To remove a vendor from the group, select the vendor and select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected vendor:

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor you want to work with.
1. On the Action Pane, open the **Vendor** tab and, from the **Rebate management** group, select **Rebate management groups**.
1. The **Rebate management groups** page opens, showing a list of groups that the selected vendor already belongs to.
1. To add the vendor to a new group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Rebate management group** - Select the group you want to add.
    - **Description** - Enter a description of the group, for example to explain why this vendor is a member of it.
1. To remove a vendor from a group, select the group and then select **Delete** on the Action Pane.

## Item rebate groups

Grouping items gives greater flexibility for calculating rebates and deductions by groups of items. It is often a more efficient method of setting up rebates and deductions for customers and vendors.

### Set up item groups

To work with rebate management item groups, go to **Rebate management \> Rebate management groups setup \> Item groups**. Use commands on the Action Pane to add and remove groups as needed. For each group, make the following settings:

- **Rebate management group** - Enter a unique name for the group.
- **Description** - Enter a description of the group to provide more information about how it should be used.

### Manage item group assignments

Each item can belong to any number of rebate management groups. You can view and assign group members starting either from the groups list or from the item list. You can also add items based on your category hierarchy.

To view, add, or remove items for a selected group:

1. Go to **Rebate management \> Rebate management groups setup \> Item groups**.
1. Select the group you want to manage.
1. From the Action Pane, select **Items**. The **Rebate management groups** page opens, showing a list of items that are already members of the selected group.
1. To add a new item to the group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Item account** - Select the item account ID.
    - **Product name** - Enter a name and/or description of the item.
1. To remove a item from the group, select the item and select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected item:

1. Go to **Product information management \> Products \> Released products**.
1. Select the item you want to work with.
1. On the Action Pane, open the **Product** tab and, from the **Rebate management** group, select **Rebate management groups**.
1. The **Rebate management groups** page opens, showing a list of groups that the selected item already belongs to.
1. To add the item to a new group, select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Rebate management group** - Select the group you want to add.
    - **Description** - Enter a description of the group, for example to explain why this item is a member of it.
1. To remove a item from a group, select the group and then select **Delete** on the Action Pane.

To add items to a group based on your category hierarchy:

1. Go to **Rebate management \> Rebate management groups setup \> Item groups**.
1. Select the group you want to manage.
1. From the Action Pane, select **Add items**. The **Add items** dialog box opens.
1. From the **Category hierarchy** drop-down list, select a top-level category
1. The item hierarchy opens in the left pane. Select the hierarchy level you are looking for.
1. Items from your selected hierarchy and hierarchy level are now listed in the right pane. To work with this pane:
    - Select the check box for each item you want to add.
    - Select the check box in grid header to select all the items shown.
    - Select the **Show selected** button to filer the list to show only those items you have selected so far. Select this button again to return to the full list.
1. Select **OK** to apply your item selection to the selected group.
