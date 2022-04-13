---
# required metadata

title: Set up multiple element revenue allocation
description: This topic describes how to set up the parameters for multiple element revenue allocation in Subscription billing.
author: JodiChristiansen
ms.date: 11/04/2021
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

# Set up multiple element revenue allocation

Multiple element revenue allocation lets you set up different templates that are used to calculate and allocate revenue across multiple items. This functionality can help you comply with Accounting Standards Codification Topic 606 (ASC 606) and/or International Financial Reporting Standard 15 (IFRS 15).

## Multiple element revenue allocation parameters

Use the **Multiple element revenue allocation parameters** page to set up the parameters for multiple element revenue allocation.

### Standalone selling price origin

The **Standalone selling price origin** field determines where the standalone selling price comes from. You can update the value on the **Item standalone selling price** page and on the transaction. The following options are available.

| Option | Description |
|--------|-------------|
| Amount | The standalone selling price is an amount that you specify that is more than 0 (zero). The amount is converted between the functional and originating currencies as required. |
| Base sales price | The standalone selling price matches the base sales price of the item. |
| Invoice price | The standalone selling price matches the invoice price of the item. |
| Percent of item | The standalone selling price is specified as a percentage value and is calculated based on the price of the item. If you select this option, specify the default percentage. |
| Allocate residual amount | <p>The origin of the standalone selling price is calculated as *Total contract value of parent item* – *Total standalone selling price of child items*:</p><ul><li>*Total contract value of parent item* is the net or billed amount.</li><li>*Total standalone selling price of child items* is the sum of the extended or contract standalone selling price of all child items, except the child item that uses this standalone selling price origin.</li></ul><p>If the calculated amount is a negative value, the amount is set to 0 (zero).</p><p>**Note:** This option can be selected for only one child item in the revenue split.</p> |
| None | The origin of the standalone selling price is based on the child items. This option applies to items that are defined as parent items in a revenue split template. If the **Revenue split** checkbox is selected, this option is automatically selected, and the setting can't be changed. |
| Percent of parent invoice price | The origin of the standalone selling price is a percentage of the invoice price of the parent item. You can change the default value. This option is available only for child items in a revenue split template. |
| Percent of parent standard price | The origin of the standalone selling price is a percentage of the standard price of the parent item. You can change the default value. This option is available only for child items in a revenue split template. It's the default option for child items. When the option for a child item is changed from **Percent of parent standard price** to **Percent of parent invoice price**, or from **Percent of parent invoice price** to **Percent of parent standard price**, the calculated values are also updated. |

### Account for revenue allocation rounding differences

The **Account for revenue allocation rounding differences** field specifies the account that is used to record any rounding adjustments to a contract revenue amount. It's available when recurring contract billing is used.

## Item standalone selling price

Use the **Item standalone selling price** page to specify the origin and standalone selling price of an item. The values that are specified on this page are used as the default values on the **Revenue allocation** page in multiple element revenue allocation and recurring contract billing.

### Specify item standalone selling price

To specify the standalone price for an item, follow these steps.

1. On the **Item standalone selling price** page, in the **Standalone selling price origin** field, select the origin of the standalone selling price.
2. Follow one of these steps, depending on the value that you selected in the **Standalone selling price origin** field:

    * If you selected **Percent of item**, specify the percentage in the **Percent** field.
    * If you selected **Amount**, specify the amount in the **Standalone selling price** field.

2. For each item that you want to add to the list, select **Add**.
3. In the **Item code** field, select the item code. In the **Item relation** field, select the item relation. For items where the **Revenue split** checkbox is cleared, the selected combination of an item code and an item relation must be unique.
4. Change the default value of the **Standalone selling price origin**, **Standalone selling price**, or **Percent** field as you require.
5. For each parent item that you want to add to the list, select **Add**.
6. In the **Item code** field, select the item code. In the **Item relation** field, select the item relation.
7. Select the **Revenue split** checkbox.
8. In the **Item relation** field, select the item relation. The list is updated with the parent item and all child items.
9. For the child item, change the default value of the **Standalone selling price origin**, **Percent of parent standard price**, **Percent of parent invoice price**, or **Allocate residual amount** field as you require.
10. To add several items at one time, select **Add items**.
11. Update the query to select the range of items that you want to add.
12. Select **OK**, review the list of items that you added, and select **OK**.

### Fields

The **Item standalone selling price** page contains the following fields.

| Field | Description |
|-------|-------------|
| Standalone selling price origin | <p>Select the origin of the standalone selling price:</p><ul><li>**Amount** – The standalone selling price is an amount that you specify that is more than 0 (zero). The amount is converted between the functional and originating currencies as required.</li><li>**Base sales price** – The standalone selling price matches the base sales price of the item.</li><li>**Invoice price** – The standalone selling price matches the invoice price of the item.</li><li>**Percent of item** – The standalone selling price is specified as a percentage value and is calculated based on the price of the item. If you select this option, specify the default percentage.</li></ul>**Allocate residual amount** – The origin of the standalone selling price is calculated as *Total contract value of parent item* – *Total standalone selling price of child items*:</p><ul><li>*Total contract value of parent item* is the net or billed amount.</li><li>*Total standalone selling price of child items* is the sum of the extended or contract standalone selling price of all child items, except the child item that uses this standalone selling price origin.</li></ul><p>If the calculated amount is a negative value, the amount is set to 0 (zero).</p><p>**Note:** This option can be selected for only one child item in the revenue split.</p></li><li>**None** – The origin of the standalone selling price is based on the child items. This option applies to items that are defined as parent items in a revenue split template. If the **Revenue split** checkbox is selected, this option is automatically selected, and the setting can't be changed.</li><li>**Percent of parent invoice price** – The origin of the standalone selling price is a percentage of the invoice price of the parent item. You can change the default value. This option is available only for child items in a revenue split template.</li><li>**Percent of parent standard price** – The origin of the standalone selling price is a percentage of the standard price of the parent item. You can change the default value. This option is available only for child items in a revenue split template. It's the default option for child items. When the option for a child item is changed from **Percent of parent standard price** to **Percent of parent invoice price**, or from **Percent of parent invoice price** to **Percent of parent standard price**, the calculated values are also updated.</li></ul> |
| Standalone selling price | Specify the standalone selling price of the item. This field is available when the **Standalone selling price origin** field is set to **Amount**. |
| Percent | Specify the percentage of the standalone selling price. This field is available when the **Standalone selling price origin** field is set to **Percent of item**, **Percent of parent invoice price**, or **Percent of parent standard price**. |
| Revenue split | <p>Specify whether a line uses revenue splitting:</p><ul><li>**Selected** – Only items that a revenue split template is set up for can be selected in the **Item relation** field. You can select this checkbox only for parent items of a revenue split template.</li><li>**Cleared** – The item is a standard item that doesn't use revenue split.</li></ul> |
| Relationship | A symbol indicates whether the item is a parent or child item in a revenue split. |
| Item code | <p>Select the item code: **Table** or **Group**.</p><p>If the **Revenue split** checkbox is selected, this field is set to **Table**, and the value can't be changed.</p> |
| Item relation | <p>Select an item number.</p><p>If the **Revenue split** checkbox is selected, only items that are parent items that a revenue split template is set up for are available for selection. When the parent item is selected, the list is automatically updated with the child items of that parent item.</p> |
| Parent item | For the parent item, this field shows the item number. For child items in a revenue split, it shows the item number of the parent item. |

## MEA templates

Use the **MEA templates** page to create and edit multiple element arrangement (MEA) template IDs. These IDs are used on the **Revenue allocation** page to group items together.

### Create a template

To set up an MEA template, follow these steps.

1. On the **MEA templates** page, select **New**.
1. In the **MEA template ID** field, enter a unique ID.
1. In the **Description** field, enter a description.
1. In the **Deferred contract revenue account** field, select the account that you want to use for journal entries when an MEA contract invoice is created. This field is available when recurring contract billing is enabled and used.
1. Select **Save**.
