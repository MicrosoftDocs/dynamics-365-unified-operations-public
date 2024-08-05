---
title: Rebate management groups
description: Learn how to set up Rebate management groups, which can be used during rebate calculations and can be attached to a master record.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 05/15/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: TAMRebateGroup
---

# Rebate management groups

[!include [banner](../includes/banner.md)]

Rebate management calculations can be driven by groups. Rebate management groups can be created for customers, vendors, and items. They can be attached to a master record.

## Rebate management customer groups

The calculation for a group of customers is often created for a chain of companies, such as a supermarket chain or a franchise company. This type of calculation is usually related to a rebate.

A deduction is often calculated without considering who the qualifying order was sold to. However, there are exceptions. For example, a licensee might create a deduction scheme where customer group A will receive 4 percent, but customer group B will receive only 3 percent.

### Set up customer groups

To work with Rebate management customer groups, go to **Rebate management \> Rebate management groups setup \> Customer groups**. You can use the buttons on the Action Pane to add and remove groups as required. For each group, set the following fields:

- **Rebate management group** – Enter a unique name for the group.
- **Description** – Enter a description of the group to provide more information about how it should be used.

### Manage customer group assignments

Each customer can belong to any number of Rebate management groups. To view and assign group members, you can start from either the group list or the customer list.

To view, add, or remove customers for a selected group, follow these steps.

1. Go to **Rebate management \> Rebate management groups setup \> Customer groups**.
1. Select the group to manage.
1. On the Action Pane, select **Customers**. The **Rebate management groups** page appears and shows a list of customers that are already members of the selected group.
1. To add a new customer to the group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Customer account** – Select the customer account ID.

1. To remove a customer from the group, select the customer, and then select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected customer, follow these steps.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer to work with.
1. On the Action Pane, on the **Customer** tab, in the **Rebate management** group, select **Rebate management groups**. The **Rebate management groups** page appears and shows a list of groups that the selected customer already belongs to.
1. To add the customer to a new group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Rebate management group** – Select the group to add the customer to.

1. To remove a customer from a group, select the group, and then select **Delete** on the Action Pane.

## Rebate management vendor groups

The calculation for a group of vendors is often created for a group of delivery points. This type of calculation is usually related to a rebate.

### Set up vendor groups

To work with Rebate management vendor groups, go to **Rebate management \> Rebate management groups setup \> Vendor groups**. You can use the buttons on the Action Pane to add and remove groups as required. For each group, set the following fields:

- **Rebate management group** – Enter a unique name for the group.
- **Description** – Enter a description of the group to provide more information about how it should be used.

### Manage vendor group assignments

Each vendor can belong to any number of Rebate management groups. To view and assign group members, you can start from either the group list or the vendor list.

To view, add, or remove vendors for a selected group, follow these steps.

1. Go to **Rebate management \> Rebate management groups setup \> Vendor groups**.
1. Select the group to manage.
1. On the Action Pane, select **Vendors**. The **Rebate management groups** page appears and shows a list of vendors that are already members of the selected group.
1. To add a new vendor to the group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Vendor account** – Select the vendor account ID.

1. To remove a vendor from the group, select the vendor, and then select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected vendor, follow these steps.

1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select the vendor to work with.
1. On the Action Pane, on the **Vendor** tab, in the **Rebate management** group, select **Rebate management groups**. The **Rebate management groups** page appears and shows a list of groups that the selected vendor already belongs to.
1. To add the vendor to a new group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Rebate management group** – Select the group to add the vendor to.

1. To remove a vendor from a group, select the group, and then select **Delete** on the Action Pane.

## Item rebate groups

By grouping items, you have more flexibility when rebates and deductions are calculated. This approach is often a more efficient way to set up rebates and deductions for customers and vendors.

### Set up item groups

To work with Rebate management item groups, go to **Rebate management \> Rebate management groups setup \> Item groups**. You can use the buttons on the Action Pane to add and remove groups as required. For each group, set the following fields:

- **Rebate management group** – Enter a unique name for the group.
- **Description** – Enter a description of the group to provide more information about how it should be used.

### Manage item group assignments

Each item can belong to any number of Rebate management groups. To view and assign group members, you can start from either the group list or the item list. You can also add items based on your category hierarchy.

To view, add, or remove items for a selected group, follow these steps.

1. Go to **Rebate management \> Rebate management groups setup \> Item groups**.
1. Select the group to manage.
1. On the Action Pane, select **Items**. The **Rebate management groups** page appears and shows a list of items that are already members of the selected group.
1. To add a new item to the group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Item account** – Select the item account ID.

1. To remove an item from the group, select the item, and then select **Delete** on the Action Pane.

To view, add, or remove group assignments for a selected item, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the item to work with.
1. On the Action Pane, on the **Product** tab, in the **Rebate management** group, select **Rebate management groups**. The **Rebate management groups** page appears and shows a list of groups that the selected item already belongs to.
1. To add the item to a new group, select **New** on the Action Pane to add a row to the grid. Then set the following field for the new row:

    - **Rebate management group** – Select the group to add the item to.

1. To remove an item from a group, select the group, and then select **Delete** on the Action Pane.

To add items to a group based on your category hierarchy, follow these steps.

1. Go to **Rebate management \> Rebate management groups setup \> Item groups**.
1. Select the group to manage.
1. On the Action Pane, select **Add items**.
1. In the **Add items** dialog box, in the **Category hierarchy** field, select a top-level category.
1. The item hierarchy is opened in the left pane. Select the hierarchy level that you're looking for.
1. Items from the selected hierarchy and hierarchy level are now listed in the right pane. Follow these steps to work with the pane:

    - Select the check box for each item that you want to add.
    - Select the check box on the grid header to select all the items that are listed.
    - Select the **Show selected** button to filter the grid so that it shows only the items that you've selected so far. Select the button again to return to the full list.

1. Select **OK** to apply your item selection to the selected group.
