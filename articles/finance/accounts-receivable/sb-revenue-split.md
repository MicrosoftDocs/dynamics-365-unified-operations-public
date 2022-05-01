---
# required metadata

title: Revenue split templates in Subscription billing
description: This topic explains how to set up revenue split templates for items that are sold as bundles.
author: JodiChristiansen
ms.date: 04/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---
# Revenue split templates in Subscription billing

Use the **Revenue split template** page to set up templates for revenue split. Revenue split consists of a parent item that has child items. This type of item is often sold to customers as a single item or bundle.

For example, a computer item can be created in the following way:

- **Parent item:** Subscription Silver
- **Line (child) items:**

    - Support
    - Maintenance
    - License

When you create a parent item, keep the following restrictions in mind:

- An item can be specified as a parent item only one time.
- The parent item can be selected as a child item in the same template.
- A valid template requires at least one child item.
- An item can be specified as a child item for more than one bundle item.
- Each parent-child relation must be unique.

## Create a parent item that has child items

Follow these steps to create a parent item that has child items.

1. On the **Revenue split template** page, select **New**.
1. In the **Parent item** field, select a parent item. The **Variant number** field is automatically updated. You can change the value as you require.
1. In the **Allocation method** field, select an allocation method.
1. In the **Component items** list, select **Add** to add child items.
1. If you selected **Percentage** in the **Allocation method** field, specify a percentage in the **Percentage** field.

    - If you selected **Equal amount** in the **Allocation method** field, the **Percentage** field is automatically updated so that every item has an equal percentage.
    - If you selected **Variable amount**, **Zero parent amount**, or **Zero amount** in the **Allocation method** field, the value of the **Percentage** field remains **0** (zero) and can't be changed.

1. Select **Save**.

## Fields

The **Revenue split template** page contains the following fields.

| Field | Description |
|-------|-------------|
| Parent item | Select an item number. This item becomes the parent item for the bundle item that you create. |
| Product name | The product name. |
| Allocation method | <p>Select the allocation method:</p><ul><li>**Equal amount** – The allocation percentages are automatically calculated and equally split among all the items in the template.</li><li>**Percentage** – You can specify a percentage amount for the allocation. The sum of all percentages must equal 100.</li><li>**Variable amount** – Child items that are added have a net amount of 0 (zero). The price of the child items must be specified at the transaction level.</li><li>**Zero amount** – The parent item retains its unit price and net amount. All child items have a net amount of 0 (zero).</li><li>**Zero parent amount** – The parent item has a fixed net amount of 0 (zero). All child items are treated like standard items. No validation is done to verify that the sum of child item amounts equals the parent item amount.</li></ul> |
| **Component items** | |
| Component item | Select an item number. This item is a child item. |
| Variant number | Select the variant number for the item. |
| Product name | The product name. |
| Percentage | <p>The allocation percentage for the milestone:</p><ul><li>If the **Allocation method** field is set to **Percentage**, you can specify the percentage.</li><li>If the **Allocation method** field is set to **Equal amount**, the percentage is automatically calculated so that every item in the template has an equal percentage.</li><li>If the **Allocation method** field is set to **Variable amount**, **Zero parent amount**, or **Zero amount**, the percentage is 0 (zero) and can't be edited.</li></ul><p>The value of this field can be any positive number between 0 (zero) and 100. The sum of all the percentages must equal 100.</p> |
| Total percentage | <p>The sum of values in the **Percentage** column.</p><ul><li>If the **Allocation method** field is set to **Equal amount** or **Percentage**, the sum of all the percentages must equal 100.</li><li>If the **Allocation method** field is set to **Variable amount**, **Zero parent amount**, or **Zero amount**, the total percentage is 0 (zero).</li></ul> |

## Revenue split on a sales order

To create a sales order that has an item that is set up for revenue split, follow these steps.

1. On the **Sales order** page, create a sales order.
2. On the line for each item that is set up for revenue split, select the **Revenue split** checkbox. That item becomes the parent item. If the template is already set up, the child items automatically appear in the list.
3. To add more child items, select **Add revenue split child**, and select the child item that you want to add.
4. Save the order.

## Revenue split with billing schedules

To create a billing schedule that has an item that is set up for revenue split, follow these steps.

1. On the **All/Active billing schedules** page, create a billing schedule.
2. On the line for each item that is set up for revenue split, select the **Revenue split** checkbox. That item becomes the parent item. If the template is already set up, the child items automatically appear in the list.
3. To add more child items, select **Add revenue split child**, and select the child item that you want to add.
4. Continue with the steps for working with the billing schedule.

> [!NOTE]
> If the **Automatically create revenue split** option is set to **Yes** on the **Recurring contract billing parameters** page, the following actions occur:
>
> - If the line item is set up as the parent item in a revenue split template, the **Revenue split** checkbox is automatically selected.
> - The child items are automatically entered on the sales order or billing schedule line.
>
> If the **Automatically create revenue split** option is set to **No**, the behavior is as explained earlier.
