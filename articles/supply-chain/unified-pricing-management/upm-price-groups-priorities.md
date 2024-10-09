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

<!-- KFM: Intro is needed for this topic. -->

## Priority configuration

In Unified pricing management, there are some places where users can define ranks for pricing calculation.

The higher value represents higher priority for calculation searching.

There are certain places where users can define ranks for pricing calculations. These ranks can be converted into calculated priorities for search calculations. A higher value represents a higher priority.

The following table indicates the places where to configure ranks and how to convert them into calculated priorities.

| Elements | Fields | Configurable in | Calculated priority |
|--|--|--|--|
| Attributes | Rank | **Pricing management** \> **Setup** \> **Price attribute groups** \> **Price attribute groups** | Same value, no conversion |
| Price group | Rank | **Pricing management** \> **During-sales pricing** \> **Price groups** \> **All price groups** | 1000+Rank |
| Price attribute group combination | Combination rank | **Pricing management** \> **Setup** \> **Price component codes** \> **Price component codes** | Same value, no conversion |
| Price component code | Pricing sequence | **Pricing management** \> **Setup** \> **Price component codes** \> **Price trees** | 1000-Sequence |

## Priority application sequence

When calculating prices, calculated priorities are checked in a specific sequence for trade agreement, adjustment and discount respectively.

The following table outlines the sequence of priority checks for pricing rules during price calculations. The sequence is numbered from 1 to 4, which indicates the order of checks.

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

After calculation, calculated priorities can be viewed on sales order lines for applied pricing rules.

1. Select a specific sales order and select **sales order** number
1. Select the lines for checking
1. Select **Sales order line** button
1. elect **Price details** under **View** group
1. **Calculated pricing priority** for applied records of base price, margin component and discount can be displayed accordingly.

![A screenshot of a computer Description automatically generated](media/image9.png)

![A screenshot of a computer Description automatically generated](media/image10.png)

![A screenshot of a computer Description automatically generated](media/image11.png)
