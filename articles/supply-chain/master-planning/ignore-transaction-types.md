---
title: Exclude specific transactions or transaction types from master planning
description: Learn how to exclude specific transactions or transaction types from master planning calculations.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/16/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Exclude specific transactions or transaction types from master planning

[!include [banner](../includes/banner.md)]

This topic describes how to exclude specific transactions or transaction types from master planning calculations.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- One or both of the following features (depending on which functionality you need) must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *Ignore specific transaction types using Planning Optimization* – Lets you select which transaction types should be excluded from master planning calculations.
    - *Exclude specific sales orders or sales order lines in Planning Optimization* – Lets you choose not to create supply for a specific sales order or sales order line when using Planning Optimization. This lets you keep an order unplanned, which can be useful for orders that require a review or approval process.

## Set a master plan to ignore specific transaction types

When the *Ignore specific transaction types using Planning Optimization* feature is enabled, you can set up each master plan to exclude specific transaction types.

1. Go to **Master planning** \> **Setup** \> **Plans**.
1. Select an existing master plan or create a new one.
1. Set **Exclude specific transactions** to *Yes*. The settings in the next step have no effect if **Exclude specific transactions** is set to *No*. <!--KFM: We have several other "include" settings here that aren't part of this feature. Are they also affected by this setting? Maybe we should also mention them here, since this is a topic about excluding things from plans? -->
1. Make the following settings on your new or selected master plan:
    - **Include sales orders** – <!--KFM: description needed. -->
    - **Include transfer orders** – Set to *No* to ignore all existing transfer orders, which means that master planning will replan transfer orders for requirements that need to be transferred <!--KFM: More detail needed here. --> (which may be useful for simulation scenarios). Set to *Yes* to include transfer orders as supply.
    - **Include purchase returns** – When a purchase order is returned in a date in the future <!--KFM: I don't understand this. Are we talking about returned SALES orders? What do we mean about "date in the future"? -->, it can be picked up for another customer order. Useful for high value goods like jewelry or watches where the return of an order must be taken into account to not over purchase, where a single item in stock is high value.
    - **Include retail sales orders** – Set to *No* to ignore orders originating from the Retail module. Set to *Yes* to include orders originating from the Retail module as supply. <!--KFM: I don't think we have a Retail module anymore. Are you referring to Dynamics 365 Commerce -->

## Exclude specific sales orders or sales order lines from master planning

When the *Exclude specific sales orders or sales order lines in Planning Optimization* feature is enabled, you can set each sales order and/or sales order line to be included in master planning calculations. This may be useful when you are using certain approval processes (such as for high-value items or high customer price) or other confirmation workflows where supply shouldn't be planned until an order is cleared.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Select an existing sales order or create a new one.
1. If you'd like to exclude the entire order from master planning, follow these steps: <!--KFM: Does this override each line setting, or just establish the default for new lines? -->
    1. Open the **Header** tab.
    1. On the **Master planning** FastTab, set **Exclude from master planning** to *Yes*.
1. If you'd like to exclude one or more order lines from master planning, follow these steps:
    1. Open the **Lines** tab.
    1. On the **Sales order lines** FastTab, select the order line you want to exclude.
    1. On the **Line details** FastTab, open the **Sourcing** tab and set **Exclude from master panning** to *Yes*.
