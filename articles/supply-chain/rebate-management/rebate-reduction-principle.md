---
# required metadata

title: Rebate reduction principles
description: 
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateCategory
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

# Rebate reduction principles

[!include [banner](../includes/banner.md)]

You can group Rebate management deals into *reduction principles* to reduce other provisions associated with an item and/or to reduce the resulting values of rebate calculations. Once you have the rebate principles set up, you can assign them as needed to the lines of your various Rebate management deals (the setting is optional). The Rebate principle rules only apply where rebate deals overlap and may therefore grant multiple rebates where they should not be owed.

## Manage rebate principles

To work with rebate principles, go to **Rebate management \>  Setup \> Rebate principles**. Use commands on the Action Pane to add and remove principles as needed. For each principle, make the settings described in the following table.

| Setting | Description |
| --- | --- |
| **Rebate principle** | Enter a unique name for the rebate principle. |
| **Description** | Enter a description of the rebate principle. |
| **Apply Reduction** | Select this check box to apply the **Reduction basis** setting for rebates within this rebate principle. |
| **Reduction basis** | When **Apply Reduction** is enabled, use this setting to specify the reduction basis. Options are *Provision* , *Rebates* or *Both*. If you select *Both*, and both a provision and rebate have been posted for a previous deal, then only the rebate will be applied. |
| **Exclude from reduction** | When this check box is selected, provisions and rebates within this rebate principle will be excluded from subsequent reductions. The **Reduction basis** doesn't apply to this setting. |

## Rebate reduction principle setup examples

The following table provides examples of various rebate reduction principle setups and the effects they will have. Each option may apply the reduction on the rebate. The rebate deduction by be based on provision, rebates, or both, and could exclude a deal from reduction or not.

The following table provides some typical examples of rebate principle settings. The purpose of each is summarized in its **Description** column.

| Rebate principle | Description | Apply reduction | Reduction basis | Exclude from reduction |
| --- | --- | --- | --- | --- |
| Deferred | Reduce rebate | Yes | Both | No |
| Exclreb | Exclude rebate | Yes | Rebate | Yes |
| Multiple | Multiple rebates | Yes | Both | Yes |
| None | Prov and Rebate only | No | Both | Yes |
| Provision | Provision only | Yes | Provision | No |
| Rebate | Rebate only | Yes | Rebate | Yes  |

## Rebate reduction principle calculation examples

Suppose you have a sales order with a single sales order line that has a value of $1,000, and that the following deals apply to this order:

- Deal 1 = 10% on $1,000
- Deal 2 = 15% on $1,000
- Deal 3 = 20% on $1,000
- Deal 4 = 25% on $1,000

The order of processing is very important. For example, if you use the order 1, 2, 3, 4, and only process the provisions, the following table summarizes the result. The processing order is based on the way you work, as described in [Process, review, and post rebates](process-review-post.md).

| Deal | Description and settings | Provision result |
| --- | --- | --- |
| 1 | Classification doesn't check other deals for reduction to take place. Checking is done for both (provision and rebates).<ul><li>**Apply reduction** - *No*</li><li>**Reduction basis** - *Both*</li><li>**Exclude from reduction** - *No*</li><ul> | $1,000 \* 10% = $100 |
| 2 | Classification checks other deals for reduction but is flagged to be ignored itself. Checking is done for rebates only.<ul><li>**Apply reduction** - *Yes*</li><li>**Reduction basis** - *Rebate*</li><li>**Exclude from reduction** - *Yes*</li><ul>| $1,000 \* 15% = $150 |
| 3 | Classification checks other deals for reduction. Checking is done for both.<ul><li>**Apply reduction** - *Yes*</li><li>**Reduction basis** - *Both*</li><li>**Exclude from reduction** - *No*</li><ul> | ($1,000 - Deal 1) \* 20% = $180 |
| 4 | Classification checks other deals for reduction. Checking is done for both.<ul><li>**Apply reduction** - *Yes*</li><li>**Reduction basis** - *Both*</li><li>**Exclude from reduction** - *No*</li><ul> | ($1,000 – Deal 1 – Deal 3) \* 25% = $180 |

The following table provides examples that show the provision processed in different sequences and the difference in the total achieved. There is variance between the provision based on the order in which the system processes the deals. It is important to understand how the sequence of processing affects the deduction amount.

| Sequence | Calculation |
| --- | --- |
| 1<br>(1, 2, 3, 4) | **Deal 1**: $1,000 \* 10% = $100<br>**Deal 2**: $1,000 \* 15% = $150<br>**Deal 3**: ($1,000 - Deal 1) \* 20% = $180<br>**Deal 4**: ($1,000 - Deal 1 - Deal 2) \* 25% = $180<br>**Total provision** = $610 |
| 2<br>(4, 3, 2, 1) | **Deal 4**: $1,000 x 25% = $250<br>**Deal 3**: ($1,000 - Deal 4) \* 20% = $150<br>**Deal 2**: $1,000 x 15% = $150<br>**Deal 1**: $1,000 x 10% = $100<br>**Total provision** = $650 |
| 3<br>(3, 2, 1, 4) | **Deal 3**: $1,000 x 20% = $200<br>**Deal 2**: $1,000 x 15% = $150<br>**Deal 1**: $1,000 x 10% = $100<br>**Deal 4**: ($1,000 - Deal 3 - Deal 1) \* 25% = $175<br>**Total provision** = $625 |
| 4<br>(2, 4, 1, 3) |**Deal 2**: $1,000 \* 15% = $150<br>**Deal 4**: $1,000 \* 25% = $250<br>**Deal 1**: $1,000 \* 10% = $100<br>**Deal 3**: ($1,000 - Deal 4 - Deal 1) \* 20% = $130<br>**Total provision** = $630 |
