---
title: Revenue allocation
description: Learn how to use revenue allocation in Subscription billing, including a step-by-step process detailing how to specify the revenue allocation for billing schedules.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 11/04/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form: 
ms.dyn365.ops.version: 10.0.24
---

# Revenue allocation

This article explains how to set up revenue allocation parameters for a billing schedule. You can set up or edit revenue allocation when you create the billing schedule. When you open the **Revenue allocation** page for an active or terminated billing schedule, the fields are read-only.

## Specify the revenue allocation for a billing schedule

To specify the revenue allocation for a billing schedule, follow these steps.

1. On the **All/Active billing schedules** list page, select a billing schedule or a billing schedule line.
2. On the **Revenue allocation** tab at the top of the page, select **Revenue allocation**.
3. In the **Multiple element arrangement type** field, select the type of multiple element arrangement (MEA).
4. In the **Multiple element arrangement number** field, specify the MEA number. Then, in the **Deferred contract revenue account** field, specify the deferred contract revenue account.

    If you set the **Multiple element arrangement type** field to **Single**, the same **Multiple element arrangement number** and **Deferred contract revenue account** values apply to each line. If you set the **Multiple element arrangement type** field to **Multiple**, you can specify different **Multiple element arrangement number** and **Deferred contract revenue account** values for each line.
    
    An MEA number can be assigned only to two or more items. A single line can't have its own MEA number.

5. Select **Save**.

### Fields

The **Multiple element arrangement** page contains the following fields.

| Field | Description |
|---|---| 
| Multiple element arrangement type | <p>Select the MEA type for the transaction:</p><ul><li>**Multiple** – The line items on the transaction are part of the MEA, or more than one arrangement exists.</li><li>**None** – The transaction is a standard transaction that doesn't have any revenue allocation.</li><li>**Single** – All the items on the transaction are part of a single MEA.</li></ul> |
| Multiple element arrangement number | <p>The MEA number for the line. This field is available when the **Multiple element arrangement type** field is set to **Multiple**.</p><p>If this field is blank, and you assign an MEA number, the **Standalone selling price origin** and **Standalone selling price** fields are automatically updated based on the values from the **Item standalone selling price** page. Only the MEA numbers that are assigned to other lines on the sales order are available.</p> |
| Deferred contract revenue account | Specify the account to use for journal entries when an MEA contract invoice is created. This field is available only when recurring contract billing is used. |
| **Lines** | |
| Variant number | The variant number from the sales order. |
| Item number | The item number from the sales order. |
| Billing frequency | The frequency for the revenue allocation: **Daily**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**. |
| Quantity | The value from the sales order. |
| Contract value | The contract value. |
| Multiple element arrangement number | <p>The MEA number for the line. This field is available when the **Multiple element arrangement type** field is set to **Multiple**.</p><p>If this field is blank, and you assign an MEA number, the **Standalone selling price origin** and **Standalone selling price** fields are automatically updated based on the values from the **Item standalone selling price** page. Only the MEA numbers that are assigned to other lines on the sales order are available. If these values aren't set up for the item, the values from the **Multiple element revenue allocation parameters** page are used.</p> | 
| Standalone selling price origin | <p>The origin of the standalone selling price:</p><ul><li>**Amount** – The standalone selling price is an amount that you specify that is more than 0 (zero). The amount is converted between the functional and originating currencies as required.</li><li>**Base sales price** – The standalone selling price matches the base sales price of the item.</li><li>**Invoice price** – The standalone selling price matches the invoice price of the item.</li><li>**Percent of item** – The standalone selling price is specified as a percentage value and is calculated based on the price of the item. If this option is selected, specify the default percentage.</li><li>**Allocate residual amount** – The origin of the standalone selling price is calculated as *Total contract value of parent item* – *Total standalone selling price of child items*:</p><ul><li>*Total contract value of parent item* is the net or billed amount.</li><li>*Total standalone selling price of child items* is the sum of the extended or contract standalone selling price of all child items, except the child item that uses this standalone selling price origin.</li></ul><p>If the calculated amount is a negative value, the amount is set to 0 (zero).</p><p>**Note:** This option can be selected for only one child item in the revenue split.</p></li><li>**None** – The origin of the standalone selling price is based on the child items. This option applies to items that are defined as parent items in a revenue split template. If the **Revenue split** checkbox is selected, this option is automatically selected, and the setting can't be changed.</li><li>**Percent of parent invoice price** – The origin of the standalone selling price is a percentage of the invoice price of the parent item. This option is available only for child items in a revenue split template.</li><li>**Percent of parent standard price** – The origin of the standalone selling price is a percentage of the standard price of the parent item. This option is available only for child items in a revenue split template. When the option for a child item is changed from **Percent of parent standard price** to **Percent of parent invoice price**, or from **Percent of parent invoice price** to **Percent of parent standard price**, the calculated values are also updated.</li></ul> |
| Standalone selling price | <p>The standalone selling price for the line, in the transaction currency.</p><p>The value in the **Amount** field is either entered or calculated.</p> |
| Contract standalone selling price | The contract standalone selling price. |
| Remaining contract revenue | The remaining revenue amount for the contract. This amount is the sum of all lines that invoices haven't yet been created for. |
| Total contract revenue | The total contract revenue amount for the line. This amount is the sum of all lines, regardless of whether invoices have been created for them. |
| Deferred contract revenue account | <p>Specify the account to use for journal entries when an MEA contract invoice is created.</p><p>This field is available only when recurring contract billing is used.</p> |
| Error | Any errors that occurred for the revenue allocation. |

## Use revenue allocation on a sales order

To use the revenue allocation functionality on a sales order, follow these steps.

1. On the **All sales orders** page, create a sales order that has items.
2. On the **Invoice** tab, under **Revenue allocation**, select **Revenue allocation**.
3. In the **Multiple element arrangement type** field, select the MEA type.
4. In the **Multiple element arrangement number** field, specify the MEA number.
5. If the **Multiple element arrangement type** field is set to **Multiple**, select the lines that you want, and then select **Apply to selected**.
6. Select **Save**.

If you use revenue and expense deferrals, the deferral schedule is automatically created. You can view it on the **All deferral schedules** page.
