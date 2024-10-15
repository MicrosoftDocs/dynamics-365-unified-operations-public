---
title: Price group priorities (preview)
description: Learn how to price group priorities work and how to use them.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Price group priorities (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

In situations where more than one price calculation could apply, the system evaluates the priority of each group to decide which one should apply. This article explains how the priority is evaluated.

## Priority configuration

There are several places in the system where you're able to assign ranks for pricing calculations. Records with a higher rank have a higher priority when the system searches for a calculation.

The following table lists the pages where you can assign ranks and how they're used to calculate priorities.

| Element | Page | Field name | Calculated priority |
|--|--|--|--|
| [Price attribute](upm-price-attribute-groups.md#price-attribute-ranks) | **Pricing management** \> **Setup** \> **Price attribute groups** \> **Price attribute groups** | **Rank** | Same value (no conversion) |
| [Price group](upm-price-groups-set-up.md) | **Pricing management** \> **During-sales pricing** \> **Price groups** \> **All price groups** | **Rank** | 1000&nbsp;&plus;&nbsp;Rank |
| [Price attribute group combination](upm-price-component-code.md#rank) | **Pricing management** \> **Setup** \> **Price component codes** \> **Price component codes** | **Combination rank** | Same value (no conversion) |
| [Price component code](upm-price-structure-details.md) | **Pricing management** \> **Setup** \> **Price component codes** \> **Price trees** | **Pricing sequence** | 1000&nbsp;&minus;&nbsp;Sequence |

## Priority application sequence

When the system calculates prices, is checks for priorities in a specific sequence for trade agreements, adjustments, and discounts. The following table outlines the sequence by which pricing rules are checked during price calculations. Each sequence is numbered from 1 to 4, which indicates the order of checks.

<table>
<thead>
<tr>
<th>Pricing rule</th>
<th>Check sequence</th>
<th>Field name</th>
<th>Visible in pricing rule</th>
<th>Configured from</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">Trade agreement</td>
<td>1.</td><td>Rank</td><td>No</td><td>Price group</td>
</tr>
<tr>
<td>2.</td><td>Pricing sequence</td><td>No</td><td>Price tree</td>
</tr>
<tr>
<td>3.</td><td>Combination&nbsp;rank</td><td>Yes</td><td>Price&nbsp;component&nbsp;code</td>
</tr>
<tr>
<td>4.</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
<tr>
<td rowspan="4">Adjustment</td>
<td>1.</td><td>Rank</td><td>Yes</td><td>Price group</td>
</tr>
<tr>
<td>2.</td><td>Pricing sequence</td><td>Yes</td><td>Price tree</td>
</tr>
<tr>
<td>3.</td><td>Combination rank</td><td>Yes</td><td>Price component code</td>
</tr>
<tr>
<td>4.</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
<tr>
<td rowspan="4">Discount</td>
<td>1.</td><td>Rank</td><td>Yes</td><td>Price group</td>
</tr>
<tr>
<td>2.</td><td>Pricing sequence</td><td>Yes</td><td>Price tree</td>
</tr>
<tr>
<td>3.</td><td>Combination rank</td><td>Yes</td><td>Price component code</td>
</tr>
<tr>
<td>4.</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
</tbody>
</table>

## Check calculated priority

After a calculation, the calculated priorities are shown on sales order lines for the applied pricing rules. To find these values, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Find and open the sales order you want to check.
1. On the **Sales order lines** FastTab, select the line you want to check.
1. On the **Sales order lines** FastTab toolbar, select **Sales order line** \> **View** \> **Price details**.
1. The **Base price**, **Margin component**, and **Discount lines** each include a **Calculated pricing priority** column, which shows the calculated priority for each line shown on each FastTab.

    :::image type="content" source="media/price-details.png" alt-text="Assign a price group to a trade journal" lightbox="media/price-details.png":::

## Related information

- [Price attribute groups](upm-price-attribute-groups.md)
- [Set up price groups for Unified pricing management](upm-price-groups-set-up.md)
- [Price component codes](upm-price-component-code.md)
- [Arrange price component codes into a price structure](upm-price-structure-details.md)
