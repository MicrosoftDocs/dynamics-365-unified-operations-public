---
title: The filter pane on the On-hand list page doesn't work as expected
description: The filters in the filter pane on the "On-hand list" page don't filter results as you expect.
author: sherry-zheng
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.16
---

# The filter pane on the On-hand list page doesn't work as expected

## Symptoms

The filters in the filter pane on the **On-hand list** page don't filter results as you expect.

## Resolution

The **On-hand list** page is assembled from a detailed on-hand inventory table that includes all available dimensions. However, the list on this page is a summary. Therefore, it might combine rows from the source table by aggregating values according to the dimensions that are shown.

Filters that are set up in the filter pane apply to the source table, not to the aggregated list. This behavior can sometimes produce unexpected results, as shown in [these examples](/dynamics365/supply-chain/inventory/inventory-on-hand-list.md#examples).

However, the [filters that are provided in the grid](/dynamics365/supply-chain/inventory/inventory-on-hand-list.md#grid-filters) *do* apply to the aggregated list. These filters include both the QuickFilter at the top of the grid and the filter for each column heading.
