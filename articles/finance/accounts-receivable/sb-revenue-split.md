---
title: Revenue split templates in Subscription billing
description: Learn how to set up revenue split templates for items that are sold as bundles, including a table that defines various fields.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/20/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Revenue split templates in Subscription billing

[!INCLUDE [banner](../../includes/banner.md)]

Use the **Revenue split template** page to set up templates for revenue split. Revenue split consists of a parent item that has child items. This type of item is often sold to customers as a single item or bundle.

For example, create a computer item in the following way:

- **Parent item:** Subscription Silver
- **Line (child) items:**

  - Support
  - Maintenance
  - License

When you create a parent item, keep the following restrictions in mind:

- You can specify an item as a parent item only one time.
- You can select the parent item as a child item in the same template.
- A valid template requires at least one child item.
- You can specify an item as a child item for more than one bundle item.
- Each parent-child relation must be unique.

## Create a parent item that has child items

Follow these steps to create a parent item that has child items.

1. On the **Revenue split template** page, select **New**.
1. In the **Parent item** field, select a parent item. The **Variant number** field updates automatically. Change the value if you want.
1. In the **Allocation method** field, select an allocation method.
1. In the **Component items** list, select **Add** to add child items.
1. If you selected **Percentage** in the **Allocation method** field, specify a percentage in the **Percentage** field.

    - If you selected **Equal amount** in the **Allocation method** field, the **Percentage** field updates automatically so that every item has an equal percentage.
    - If you selected **Variable amount**, **Zero parent amount**, or **Zero amount** in the **Allocation method** field, the value of the **Percentage** field remains **0** (zero) and can't be changed.

1. Select **Save**.

## Fields

The **Revenue split template** page contains the following fields.

| Field | Description |
| ------- | ------------- |
| Parent item | Select an item number. This item becomes the parent item for the bundle item that you create. |
| Product name | The product name. |
| Allocation method | <p>Select the allocation method:</p><ul><li>**Equal amount** – The allocation percentages are automatically calculated and equally split among all the items in the template.</li><li>**Percentage** – You can specify a percentage amount for the allocation. The sum of all percentages must equal 100.</li><li>**Variable amount** – Child items that you add have a net amount of 0 (zero). You must specify the price of the child items at the transaction level.</li><li>**Zero amount** – The parent item retains its unit price and net amount. All child items have a net amount of 0 (zero).</li><li>**Zero parent amount** – The parent item has a fixed net amount of 0 (zero). All child items are treated like standard items. No validation is done to verify that the sum of child item amounts equals the parent item amount.</li></ul> |
| **Component items** | |
| Component item | Select an item number. This item is a child item. |
| Variant number | Select the variant number for the item. |
| Product name | The product name. |
| Percentage | <p>The allocation percentage for the milestone:</p><ul><li>If the **Allocation method** field is set to **Percentage**, specify the percentage.</li><li>If the **Allocation method** field is set to **Equal amount**, the percentage is automatically calculated so that every item in the template has an equal percentage.</li><li>If the **Allocation method** field is set to **Variable amount**, **Zero parent amount**, or **Zero amount**, the percentage is 0 (zero) and can't be edited.</li></ul><p>The value of this field can be any positive number between 0 (zero) and 100. The sum of all the percentages must equal 100.</p> |
| Total percentage | <p>The sum of values in the **Percentage** column.</p><ul><li>If the **Allocation method** field is set to **Equal amount** or **Percentage**, the sum of all the percentages must equal 100.</li><li>If the **Allocation method** field is set to **Variable amount**, **Zero parent amount**, or **Zero amount**, the total percentage is 0 (zero).</li></ul> |

## Revenue split on a sales order

To create a sales order that has an item that is set up for revenue split, follow these steps:

1. On the **Sales order** page, create a sales order.
2. On the line for each item that you set up for revenue split, select the **Revenue split** checkbox. That item becomes the parent item. If the template is already set up, the child items automatically appear in the list.
3. To add more child items, select **Add revenue split child**, and select the child item that you want to add.
4. Save the order.

## Revenue split with billing schedules

To create a billing schedule that has an item set up for revenue split, follow these steps:

1. On the **All/Active billing schedules** page, create a billing schedule.
2. On the line for each item that you set up for revenue split, select the **Revenue split** checkbox. That item becomes the parent item. If the template is already set up, the child items automatically appear in the list.
3. To add more child items, select **Add revenue split child**, and select the child item that you want to add.
4. Continue with the steps for working with the billing schedule.

> [!NOTE]
> If the **Automatically create revenue split** option is set to **Yes** on the **Recurring contract billing parameters** page, the following actions occur:
>
> - If you set up the line item as the parent item in a revenue split template, the **Revenue split** checkbox is selected automatically.
> - The child items are entered automatically on the sales order or billing schedule line.
>
> If you set the **Automatically create revenue split** option to **No**, the behavior is as explained earlier.

> [!NOTE]
> A feature that allows a **Billing schedule line with revenue split** to set **Renew automatically** to **Yes**.

## Additional revenue split information

When you add an item that's part of a revenue split, note the following information:

- You can't defer the parent amount.
- The start date, end date, quantity, unit, site, and warehouse values of child items are based on the parent item. You can't change these values for the child items. Make all changes to the parent item.
- The pricing method is **Flat** and can't be changed.
- You can add or remove child items.
- Parent and child items must use the same item group.
- Child items can have one of the following setups:

  - The **Billing frequency** and **Billing intervals** fields are set to the same value as the parent item.
  - The **Billing frequency** field is set to **One-time**. In this case, the **Billing intervals** field is automatically set to **1**.

- The sum of the net amounts of the child items equals the parent amount. If the allocation method is **Zero amounts**, both the sum of the child item amounts and the parent amount are 0 (zero).

    > [!NOTE]
    > If the allocation method is **Zero parent amount**, the (non-zero) sum of the child items doesn't equal parent amount, which is 0 (zero). Use this allocation method for internal purposes, so that employees can see the child items. However, customers can only see the parent item.

- If the multiple element arrangement (MEA) type of the sales order is **Single**, the corresponding multiple element revenue allocation transaction line is created when you add the parent and child items.
- If the allocation method for a revenue split is **Equal amounts**, and you change the parent amount, the amounts are recalculated for all child lines.
- For a revenue split where the allocation method is **Variable amount**, the following behavior occurs:

  - The net amount of the parent item appears in the **Parent amount** column. You can edit this value. However, the unit price, net amount, and discount are 0 (zero) and can't be edited.
  - The unit price of child items is 0 (zero). You can edit the unit price or net amount. When you edit one value, the other value is automatically updated.

- For a revenue split where the allocation method is **Percentage**, the following behavior occurs:

  - The net amount of the parent item appears in the **Parent amount** column. You can edit this value. However, the unit price, net amount, and discount are 0 (zero) and can't be edited.
  - The net amount of child items is calculated as *Percentage* &times; *Parent amount*.

- For a revenue split where the allocation method is **Equal amount**, the following behavior occurs:

  - The net amount of the parent item appears in the **Parent amount** column. You can edit this value. However, the unit price, net amount, and discount are 0 (zero) and can't be edited.
  - The net amount of child items is calculated by dividing the parent amount equally among all the child items.
  - If you remove or add child items, the net amount and unit prices are recalculated so that all child lines have equal amounts.
  - If the parent amount can't be divided equally, the net amount and unit price of the last child item might be slightly more or less than the net amount and unit price of the other child items.

- For a revenue split where the allocation method is **Zero amount**, the following behavior occurs:

  - You can edit the unit price, net amount, and discount. The parent amount is 0 (zero) and can't be edited.
  - The quantity, unit, site, and warehouse values of child items are based on the parent item. You can't change these values for the child items. Make all changes to the parent item.
  - The unit price and net price of child items is 0 (zero) and can't be edited.

- For a revenue split where the allocation method is **Zero parent amount**, the following behavior occurs:

  - The unit price, parent amount, and net amount of the parent item are 0 (zero).
  - In a billing schedule, the child lines appear as if you manually added them, and all values are updated based on the selected billing schedule group. You can edit these values. For child items, you can access the **Escalation and discount** and **Advanced pricing** options by using the **Quantity entered**, **Unit price**, **Discount**, and **Net amount** fields in **View billing details**.
  - On a sales order, the child lines have a discount and discount percentage of 0 (zero).
  - You can change the billing frequency of the parent and the child items, and each line can have a different frequency. However, the parent item is automatically updated so that it uses the shortest frequency from among its child lines. For example, a revenue split has two child items, one of which uses the **Monthly** billing frequency and the other of which uses the **Annually** billing frequency. In this case, the billing frequency of the parent item is updated to **Monthly**.
