---
# required metadata

title: Merge inventory batches
description: This article provides information about how to consolidate two or more inventory batches into a merged batch.
author: yufeihuang
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventBatchJournalListPage, InventBatchJournalMerge
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 39782
ms.assetid: 07c5e98b-10fd-4f5c-b471-41d2150f47b0
ms.search.region: Global
# ms.search.industry:
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Merge inventory batches

[!include [banner](../includes/banner.md)]

This article provides information about how to consolidate two or more inventory batches into a merged batch.

When you merge batches, calculations can help optimize the characteristics and batch attributes of the merged batch. After you select the source batches, you can review and change the merged batch before you post it. You can also transfer the batch merge to an inventory journal for approval. Inventory can then be reserved or posted directly from that inventory journal. When you post a merged batch, the inventory is adjusted for the source batches and the merged batch.

## Are there any prerequisites?
Yes, there are some things that you must set up before you can use the merge batch tools. The following table describes the prerequisites.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Page</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Journal names, inventory</td>
<td>You must create a journal name of the type BOM that is used by default when you post batch merges in inventory journals. Optional but recommended: You can specify that reservations should be made automatically when the batch merge is transferred to the inventory journal. Otherwise, there is a risk that the on-hand inventory might be changed after the batch merge details are set up and the journal is posted. To enable automatic reservations for the journal name, select <strong>Automatic</strong> in the <strong><strong>Reservation</strong></strong> field.</td>
</tr>
<tr class="even">
<td>Inventory and warehouse management parameters</td>
<td>You must specify the default journal name for the inventory journal.</td>
</tr>
<tr class="odd">
<td>Released products</td>
<td>Here are the recommended settings for the item:
<ul>
<li>To automatically generate batch numbers for merged batches, you must assign the released product to a batch number group. You can also enter a batch number manually when you create a merged batch, or select an existing batch number. If you select an existing batch number, make sure that the selected batch hasn&#39;t been included in any inventory transactions.</li>
<li>If you&#39;re using shelf life or best-before dates for the released product, the dates for a merged batch are calculated based on the selection in the <strong>Batch merge date calculation</strong> field. The following options are available:
<ul>
<li><strong>Earliest</strong> – The calculation is based on the earliest date that is specified for a source batch that is selected for the batch merge.</li>
<li><strong>Latest</strong> – The calculation is based on the latest date that is specified for a source batch that is selected for the batch merge.</li>
<li><strong>Manual</strong> – No calculation is done. If a date is the same on all source batches, a date is suggested. You can change that date. If a date isn&#39;t the same on the source batches, you can manually enter the date.</li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>Batch number group</td>
<td>Optional: To generate a batch number when you create a merged batch, you must assign a batch number group to the released product. Otherwise, you can enter a batch number manually.</td>
</tr>
</tbody>
</table>

## When might I want to merge batches of inventory?
Here are some examples of scenarios where it might be useful to merge batches:

-   Walking through the warehouse, Sammy notices that several batches of the same item have low quantities. Sammy is expecting to receive several new shipments, and realizes that some floor space can be freed by merging the odd quantities into a new batch.
-   Sammy is receiving inventory, and wants to combine the new batch with one that has already been received, to improve the batch attribute value of the existing batch. By doing so you create a new batch.

## Can I merge batches across sites and legal entities?
No, you can merge only batches that have the same site and warehouse storage dimensions in one legal entity. However, you can specify a different location and pallet ID for the merged batch.

## Can I merge partial quantities?
No, you can merge only the full quantity of batches. The batch merge functionality is intended as an inventory feature, not a production feature.

## What if the batches have different batch attribute values?
When you select the source batches to combine in the merged batch, Supply Chain Management verifies whether all the batches have the characteristics or attribute values. When an attribute value is the same, a value is suggested for the merged batch. You can change that value. Attribute values that aren't the same are left blank for the merged batch, and you can enter those values manually. If the batch attribute type for the attribute value is an integer or a fraction, and the values aren't the same for all the source batches, the value is calculated by using a weighted average calculation. The calculated value is rounded up or down to the nearest increment. If the value is blank for a source batch, the batch and its quantity aren't included in the calculation. **Example** The following example shows a weighted average calculation for a merged batch. Two of the source batches have a blank value for a batch attribute type that is an integer. The following attribute is assigned to the source batches.

| Attribute | Minimum | Increment | Maximum |
|-----------|---------|-----------|---------|
| Grade     | 3       | 3         | 30      |

The source batches have the following attribute values for the **Grade batch** attribute.

| Batch | Quantity | Attribute | Attribute value |
|-------|----------|-----------|-----------------|
| B1    | 10       | Grade     | Blank           |
| B2    | 15       | Grade     | 15              |
| B3    | 20       | Grade     | 20              |
| B4    | 25       | Grade     | Blank           |
| B5    | 30       | Grade     | 25              |

When you add these batches as source batches, the following values are assigned to the merged batch.

| Batch | Quantity | Attribute | Attribute value |
|-------|----------|-----------|-----------------|
| B6    | 100      | Grade     | 21              |

The values and quantities for batches B1 and B4 aren't included in the weighted average calculation. Therefore, here is how the value for the merged batch is calculated.

| Value | Quantity (weight)                              | Relative weight | Relative weight × Value                                               |
|-------|------------------------------------------------|-----------------|-----------------------------------------------------------------------|
| 15    | 15                                             | 0.230769231     | 3.461538462                                                           |
| 20    | 20                                             | 0.307692308     | 6.153846154                                                           |
| 25    | 30                                             | 0.461538462     | 11.53846154                                                           |
|       | **Total:** 65, which is the sum of the weights |                 | **Total:** 21.5384615, which is rounded to 21 (the nearest increment) |

## What if the batches have different batch dates?
If the batches have different batch dates, some of the dates are calculated based on the values in the **Batch dates** group on the **Merged batch** FastTab of the **Batch merge** page. The system calculates values for the fields in the **Batch dates** group. These values include the manufacturing date, expiration date, shelf advice date, and best-before date. The dates are calculated based on settings for the item in the **Item data** field group of the **Released product details** page. You can change the values or enter them manually. For all other dates, no calculation is done. The same principle is used for batch attribute values. If a date is the same for all the source batches, that date is suggested for the merged batch. If the date isn't the same for all source batches, the date is blank on the merged batch, and you can enter it manually.

## What if the dimensions are different on the batches that I want to merge?
Here is how product dimensions, tracking dimensions, and storage dimensions are handled:

-   **Product dimensions** – All product dimensions for the selected item must be the same. You can't merge batches across product dimensions.
-   **Tracking dimensions** – A new batch number is automatically generated if a batch number group is specified for the item. If a batch number group isn't assigned to an item, you can select an existing batch or enter the number manually. Serial numbers are transferred from the source batch to the inventory journal lines for the merged batch.
-   **Storage dimensions** – The site and warehouse storage dimensions must be the same for all the source batches and the merged batch. However, you can specify a new location and pallet ID for the merged batch.

## How does posting work?
Posting works in two ways, depending on whether you use an approval process for journals. You can use the **Transfer to journal** and **Post the batch merge** actions to transfer the batch merge to a journal where it can be verified and posted, or you can post the batch merge directly. The main difference between the two actions is that a transfer to a journal doesn't post the batch merge. Both actions create a new batch if an existing batch isn't selected, update all batch details and attribute values, and create an inventory journal.

-   **Transfer to journal** – Transfer the batch merge details to a new inventory journal. If you've set up automatic reservations, the quantities in the source batches are reserved. The details of the batch merge can't be changed. To modify the batch merge, you must delete the journal. The journal can be used as a task that another employee must perform later. The reservation of the batch quantity to the journal line is secured. This allocation lets a quality planner or a warehouse manager create tasks for their employees.
-   **Post the batch merge** – Post the batch merge directly. This action can be performed after the physical merge has occurred.

You can approve the inventory journal for the batch merge from the **All batch merges** list page. Click **Journal** &gt; **Post**. After a journal is posted, you can't change the details in the merged batch. After you transfer a batch merge to an inventory journal, you can change the details only if the journal is deleted.

## After I merged a catchweight item, why can’t I see the catchweight information in the inventory journal?
You can merge batches of catch-weight items just like all other items. However, the catch-weight information doesn't appear in the inventory journal. We recommend that you verify the catch-weight information before you transfer the batch merge to the inventory journal.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
