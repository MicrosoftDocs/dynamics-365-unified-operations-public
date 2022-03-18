---
title: Functional gaps between inventory value/aging reports and their storage versions
description: Functional gaps between inventory value/aging reports and their storage versions
author: AndersGirke
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.15
---

# Functional gaps between inventory value/aging reports and their storage versions

The [Inventory aging report storage](/dynamics365/supply-chain/cost-management/inventory-aging-report-storage.md) and [Inventory value storage report](/dynamics365/supply-chain/cost-management/inventory-value-report-storage.md) features enable Supply Chain Management to display large volumes of inventory transactions. In each case, the report results are saved for browsing and exporting, unlike with the non-storage versions of these reports. However, some functionality that exists in the non-storage versions of these reports doesn't exist in the storage versions. The following subsections summarize the differences and provide workarounds.

## Storage reports don't include subtotals, even if they are enabled in the report layout

Subtotals can cause issues when the result is exported, especially if users change the record sequence.

To check the subtotals, you can export the result into Microsoft Excel. Alternatively, if you want to check subtotals within Supply Chain Management, use [Feature management](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *New grid control* and *Grouping in grids* features, which provide a much more flexible way to see the subtotal for any group by column. For more information, see [Grid capabilities](/dynamics365/fin-ops-core/fin-ops/get-started/grid-capabilities.md).

## Inventory value storage report doesn't support ledger account information

You can run the trial balance to get the inventory accounts balance and compare that to the **Inventory value storage** report.
