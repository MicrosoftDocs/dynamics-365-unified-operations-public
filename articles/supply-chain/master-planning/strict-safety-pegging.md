---
title: Strict safety stock pegging
description: XXXX
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/10/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# Safety stock pegging

[!include [banner](../includes/banner.md)]

You can choose how strictly the system should peg safety stock as demand against the planned order created for it.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The feature that is named *Strict safety stock pegging for Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set safety stock pegging options

| Master planning | (Preview) Strict safety stock pegging for Planning Optimization | Gives you the option of directly pegging safety stock as demand against the planned order created for it. 

On the **Coverage groups** page, this feature adds a new parameter called **Strict safety stock pegging**, which lets you choose one of the following options for each coverage group:

- *No*: Safety stock is considered the least important of type of demand, so whenever a planned order is created for safety stock, all other demand will be prioritized, which lets you provide a higher service level for your customers. This is how the system always behaved in previous versions.
- *Yes*: The system will apply strict safety stock pegging. When a planned order is created for fulfilling safety stock, it will always be pegged against safety stock, without allowing any other demand to be pegged against it (except when using a **Coverage code** of *Period*). This can provide better visibility in some scenarios, such as when you're using a high number of negative days.
