---
title: Exclude specific transactions or transaction types from master planning
description: Learn how to exclude specific transactions or transaction types from master planning calculations, including prerequisites.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 01/16/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Exclude specific transactions or transaction types from master planning

[!include [banner](../includes/banner.md)]

This article describes how to exclude specific transactions or transaction types from master planning calculations.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- Depending on the functionality that you require, one or both of the following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

    - *Ignore specific transaction types using Planning Optimization* – This feature lets you select which transaction types should be excluded from master planning calculations.
    - *Exclude specific sales orders or sales order lines in Planning Optimization* – This feature lets you choose not to create supply for a specific sales order or sales order line when you use Planning Optimization. In this way, you can keep an order unplanned. This capability can be useful for orders that require a review or approval process. As of Supply Chain Management version 10.0.43, this feature is turned on by default.

## Set a master plan to ignore specific transaction types

When the *Ignore specific transaction types using Planning Optimization* feature is enabled, you can set up each master plan to exclude specific transaction types.

1. Go to **Master planning** \> **Setup** \> **Plans**.
1. Select an existing master plan, or create a new one.
1. Set the **Exclude specific transactions** option to *Yes*. If this option is set to *No*, the settings in the next step have no effect.
1. Set the following fields for the new or selected master plan:

    - **Include sales orders** – Set this option to *No* to ignore all existing sales orders. Set it to *Yes* to plan supply for sales orders.
    - **Include transfer orders** – Set this option to *No* to ignore all existing transfer orders. In this case, master planning replans transfer orders for requirements that must be transferred. (This behavior might be useful for simulation scenarios.) Set this option to *Yes* to include transfer orders as supply.
    - **Include purchase returns** – When a purchase order is scheduled to be returned at a future date, it can be picked up for another customer order. This capability is useful for high-value items such as jewelry or watches. In these cases, the return of an order must be considered to avoid over-purchasing the high-value item.
    - **Include retail sales orders** – Set this option to *No* to ignore orders that originate from the **Commerce** module. Set it to *Yes* to include orders that originate from the **Commerce** module as supply.

## Exclude specific sales orders or sales order lines from master planning

When the *Exclude specific sales orders or sales order lines in Planning Optimization* feature is enabled, you can set each sales order and/or sales order line so that it's included in master planning calculations. This capability might be useful when you use some approval processes (such as the approval process for high-value items or high customer prices). It might also be useful in other confirmation workflows where supply shouldn't be planned until an order is cleared.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Select an existing sales order, or create a new one.
1. To exclude the whole order from master planning, on the **Header** tab, on the **Master planning** FastTab, set the **Exclude from master planning** option to *Yes*. This setting defines the default value for new lines, but it doesn't override the value on existing lines.
1. To exclude one or more order lines from master planning, follow these steps:

    1. On the **Lines** tab, on the **Sales order lines** FastTab, select the order line that you want to exclude.
    1. On the **Line details** FastTab, on the **Sourcing** tab, set the **Exclude from master planning** option to *Yes*.
