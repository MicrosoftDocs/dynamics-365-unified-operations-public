---
title: Rebate reduction principles
description: Learn how to set up reduction principles, which control the behavior when multiple rebates apply to the same item or transaction.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 05/15/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: TAMRebateCategory
---

# Rebate reduction principles

[!include [banner](../includes/banner.md)]

You can group Rebate management deals into *reduction principles* to reduce other provisions that are associated with an item, and/or to reduce the resulting values of rebate calculations. After the rebate reduction principles are set up, you can optionally assign them, as required, to the lines of your Rebate management deals.

The rebate reduction principle rules apply only when rebate deals overlap. Therefore, they might grant multiple rebates in situations where multiple rebates aren't owed.

## Manage rebate reduction principles

To work with rebate reduction principles, go to **Rebate management \> Setup \> Rebate reduction principles**. Then use the buttons on the Action Pane to add and remove reduction principles as required. For each principle, set the fields as described in the following table.

| Field | Description |
|---|---|
| Rebate reduction principle | Enter a unique name for the rebate reduction principle. |
| Description | Enter a description of the rebate reduction principle. |
| Apply reduction | Select this check box to apply a reduction basis to rebates that belong to this rebate reduction principle. |
| Reduction basis | If you selected the **Apply reduction** check box, select the reduction basis (*Provision*, *Rebates*, or *Both*). If you select *Both*, and if both a provision and a rebate have been posted for a previous deal, only the rebate will be applied. |
| Exclude from reduction | If this check box is selected, provisions and rebates that belong to this rebate reduction principle will be excluded from subsequent reductions. The setting of the **Reduction basis** field doesn't apply to this setting. |

## Examples of rebate reduction principle setups

The following table shows some typical examples of rebate reduction principle setups. For each of these rebate reduction principles, the value of the **Description** field describes the purpose of the rebate reduction principle.

| Rebate reduction principle | Description | Apply reduction | Reduction basis | Exclude from reduction |
|---|---|---|---|---|
| Deferred | Reduce rebate | Yes | Both | No |
| Exclreb | Exclude rebate | Yes | Rebate | Yes |
| Multiple | Multiple rebates | Yes | Both | Yes |
| None | Prov and Rebate only | No | Both | Yes |
| Provision | Provision only | Yes | Provision | No |
| Rebate | Rebate only | Yes | Rebate | Yes |

## Examples of rebate reduction principle calculations

You have a sales order that has a single sales order line. This line has a value of $1,000. The following deals apply to the order:

- **Deal 1:** 10 percent on $1,000
- **Deal 2:** 15 percent on $1,000
- **Deal 3:** 20 percent on $1,000
- **Deal 4:** 25 percent on $1,000

The order of processing is very important. The processing order is based on the way that you work, as described in [Process, review, and post rebates](process-review-post.md).

For example, the following table summarizes the result if you use the order *1, 2, 3, 4*, and if you process only the provisions.

| Deal | Description and settings | Provision result |
|---|---|---|
| 1 | <p>The classification doesn't check other deals for reductions. The check is done for both provisions and rebates.</p><ul><li>**Apply reduction:** *No*</li><li>**Reduction basis:** *Both*</li><li>**Exclude from reduction:** *No*</li></ul> | $1,000 × 10% = $100 |
| 2 | <p>The classification checks other deals for reductions but is flagged so that it itself is ignored. The check is done only for rebates.</p><ul><li>**Apply reduction:** *Yes*</li><li>**Reduction basis:** *Rebate*</li><li>**Exclude from reduction:** *Yes*</li></ul> | $1,000 × 15% = $150 |
| 3 | <p>The classification checks other deals for reductions. The check is done for both provisions and rebates.</p><ul><li>**Apply reduction:** *Yes*</li><li>**Reduction basis:** *Both*</li><li>**Exclude from reduction:** *No*</li></ul> | ($1,000 – Deal 1) × 20% = $180 |
| 4 | <p>The classification checks other deals for reductions. The check is done for both provisions and rebates.</p><ul><li>**Apply reduction:** *Yes*</li><li>**Reduction basis:** *Both*</li><li>**Exclude from reduction:** *No*</li></ul> | ($1,000 – Deal 1 – Deal 3) × 25% = $180 |

The following table shows some examples where the provision is processed in different orders, and where different totals are therefore achieved. The variance in the provisions depends on the order that the system processes the deals in. It's important that you understand how the order of processing affects the final rebate amount.

| Sequence | Calculation |
|---|---|
| 1<br>(1, 2, 3, 4) | <ul><li>**Deal 1:** $1,000 × 10% = $100</li><li>**Deal 2:** $1,000 × 15% = $150</li><li>**Deal 3:** ($1,000 – Deal 1) × 20% = $180</li><li>**Deal 4:** ($1,000 – Deal 1 – Deal 2) × 25% = $180</li><li>**Total provision:** $610</li></ul> |
| 2<br>(4, 3, 2, 1) | <ul><li>**Deal 4:** $1,000 x 25% = $250</li><li>**Deal 3:** ($1,000 – Deal 4) × 20% = $150</li><li>**Deal 2:** $1,000 x 15% = $150</li><li>**Deal 1:** $1,000 x 10% = $100</li><li>**Total provision:** $650</li></ul> |
| 3<br>(3, 2, 1, 4) | <ul><li>**Deal 3:** $1,000 x 20% = $200</li><li>**Deal 2:** $1,000 x 15% = $150</li><li>**Deal 1:** $1,000 x 10% = $100</li><li>**Deal 4:** ($1,000 – Deal 3 – Deal 1) × 25% = $175</li><li>**Total provision:** $625</li></ul> |
| 4<br>(2, 4, 1, 3) | <ul><li>**Deal 2:** $1,000 × 15% = $150</li><li>**Deal 4:** $1,000 × 25% = $250</li><li>**Deal 1:** $1,000 × 10% = $100</li><li>**Deal 3:** ($1,000 – Deal 4 – Deal 1) × 20% = $130</li><li>**Total provision:** $630</li></ul> |
