---
title: Price group priorities (preview)
description: Learn how price group priorities work and how to use them.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Price group priorities (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

In situations where more than one price calculation can apply, the system evaluates the priority of each group to determine which one should apply. This article explains how the priority is evaluated.

## Priority configuration

You can assign ranks for pricing calculations in several places. Records that you assign a higher rank to have a higher priority when the system searches for a calculation.

The following table lists the pages where you can assign ranks. It also shows how the ranks that are assigned on each page are used to calculate priorities.

| Element | Page | Field name | Calculated priority |
|---|---|---|---|
| [Price attribute](upm-price-attribute-groups.md#price-attribute-ranks) | Price attribute groups<br>(**Pricing management** \> **Setup** \> **Price attribute groups** \> **Price attribute groups**) | Rank | Same value (No conversion is done.) |
| [Price group](upm-price-groups-set-up.md) | All price groups<br>(**Pricing management** \> **During-sales pricing** \> **Price groups** \> **All price groups**) | Rank | 1,000 &plus; *Rank* |
| [Price attribute group combination](upm-price-component-code.md#rank) | Price component codes<br>(**Pricing management** \> **Setup** \> **Price component codes** \> **Price component codes**) | Combination rank | Same value (No conversion is done.) |
| [Price component code](upm-price-structure-details.md) | Price trees<br>(**Pricing management** \> **Setup** \> **Price component codes** \> **Price trees**) | Pricing sequence | 1,000 &minus; *Sequence* |

## Priority application sequence

When the system calculates prices, it checks for priorities for trade agreements, adjustments, and discounts in a specific sequence. The following table outlines the sequence that the system uses to check pricing rules during price calculations. Each sequence is numbered from 1 through 4. These numbers indicate the order of checks.

<table>
<thead>
<tr>
<th>Pricing rule</th>
<th>Check sequence</th>
<th>Field name</th>
<th>Visible in the pricing rule</th>
<th>Configured from</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">Trade agreement</td>
<td>1</td><td>Rank</td><td>No</td><td>Price group</td>
</tr>
<tr>
<td>2</td><td>Pricing sequence</td><td>No</td><td>Price tree</td>
</tr>
<tr>
<td>3</td><td>Combination rank</td><td>Yes</td><td>Price component code</td>
</tr>
<tr>
<td>4</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
<tr>
<td rowspan="4">Adjustment</td>
<td>1</td><td>Rank</td><td>Yes</td><td>Price group</td>
</tr>
<tr>
<td>2</td><td>Pricing sequence</td><td>Yes</td><td>Price tree</td>
</tr>
<tr>
<td>3</td><td>Combination rank</td><td>Yes</td><td>Price component code</td>
</tr>
<tr>
<td>4</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
<tr>
<td rowspan="4">Discount</td>
<td>1</td><td>Rank</td><td>Yes</td><td>Price group</td>
</tr>
<tr>
<td>2</td><td>Pricing sequence</td><td>Yes</td><td>Price tree</td>
</tr>
<tr>
<td>3</td><td>Combination rank</td><td>Yes</td><td>Price component code</td>
</tr>
<tr>
<td>4</td><td>Attribute rank</td><td>No</td><td>Price attribute group</td>
</tr>
</tbody>
</table>

## Review calculated priorities

After a calculation, the calculated priorities are shown on sales order lines for the applied pricing rules. To review the calculated priority values, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Find and open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line that you want to check.
1. On the toolbar of the **Sales order lines** FastTab, select **Sales order line** \> **View** \> **Price details**.

    On the **Price details** page, each grid (**Base price**, **Margin component**, and **Discount lines**) includes a **Calculated pricing priority** column. This column shows the calculated priority of each line in the grid.

    :::image type="content" source="media/price-details.png" alt-text="Screenshot of the Price details page, highlighting the Calculated pricing priority value for a line in the Base price grid." lightbox="media/price-details.png":::

## Related information

- [Price attribute groups](upm-price-attribute-groups.md)
- [Set up price groups for Unified pricing management](upm-price-groups-set-up.md)
- [Price component codes](upm-price-component-code.md)
- [Arrange price component codes into a price structure](upm-price-structure-details.md)
