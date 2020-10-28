---
# required metadata

title: Troubleshoot cost management
description: This topic describes how to fix issues that you might encounter while working with cost management.
author: riluan
manager: tfehr
ms.date: 10/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails, InventValueProcess, InventValueReportSetup, InventClosing
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: riluan
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Release 10.0.15

---

# Troubleshoot cost management

This topic describes how to fix issues that you might encounter while working with cost management.

## Functional gaps between the inventory value/aging reports and their storage versions

The [Inventory aging report storage](inventory-aging-report-storage.md) and [Inventory value storage report](inventory-value-report-storage.md) features enable Supply Chain Management to display large volumes of inventory transactions. In each case, the report results are saved for browsing and exporting, unlike with the non-storage versions of these reports. However, some functionality that exists in the non-storage versions of these reports doesn't exist in the storage versions. The following subsections summarize the differences and provide workarounds.

### Storage reports don't include subtotals, even if they are enabled in the report layout

Subtotals can cause issues when the result is exported, especially if users change the record sequence.

To check the subtotals, you can export the result into Microsoft Excel. Alternatively, if you want to check subtotals within Supply Chain Management, use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *New grid control* and *(Preview) Grouping in grids* features, which provide a much more flexible way to see the subtotal for any group by column. For more information, see [Grid capabilities](../../fin-ops-core/fin-ops/get-started/grid-capabilities.md).

### Inventory value storage report doesn't support ledger account information

You can run the trial balance to get the inventory accounts balance and compare that to the **Inventory value storage** report.

## Warnings or errors are shown when changing a ledger period status without closing inventory

Microsoft introduced the following validations to prevent issues caused by an incorrect period-end process around costing. If you encounter any of the following error messages, refer to [KB 4561987](https://fix.lcs.dynamics.com/Issue/Details?kb=4561987&bugId=445351&dbType=3&qc=f514f2adcddcddceec43af58c26ae8a9020effdc7cdfe085d9d0deeb8cc7b6a3) for more information about how to resolve these issues.

- You are about to execute a Recalculation with a date %1 (10-02-2019). The last registered Recalculation was executed in a previous period with a date %2 (20-01-2019). No execution of an inventory close with a date %3 (31-01-2019) matching period end has been registered. Please remember to execute an inventory close as of %3 (31-01-2019) matching the period end. The valuation of inventories, cost of goods sold and variances may not be correct in subledger or general ledger until this has been executed.

- You are about to change the status of ledger period %1 to %2. No execution of inventory close with a date %3 matching period end has been registered. Please execute an inventory close as of %3 matching the period end before changing the status. The valuation of inventories, cost of goods sold and variances may not be correct in subledger or general ledger until this has been executed. Reported from legal entity %4. For now, it is informational, but you will be required to perform such action in future.

- The Account structure %1 has been changed. One or more main accounts %2 no longer exist. These Main accounts are required by the %3 with a date %4. Please add these Main accounts to the Account structure %1 before you can resume the %3 job. For now, it is informational, but you will be required to perform such action in future.

- You are about to execute an inventory close with a date %1 (31-01-2019). No execution of backflush costing calculation with a date %2 (31-01-2019) matching period end has been registered. Please remember to execute a backflush costing calculation with a date of %3 (31-01-2019) matching period end. The valuation of inventories, cost of goods sold and variances may not be correct in subledger or general ledger until this has been executed.

- You are about to execute a backflush costing calculation with a date %1 (28-02-2019). The last registered backflush costing calculation was executed in a previous period with a date %2 (31-01-2019). No execution of an inventory close with a date %3 (31-01-2019) matching a period end has been registered.
Please remember to execute an inventory close as of %3 (31-01-2019) matching a period end. The valuation of inventories, cost of goods sold and variances may not be correct in subledger or general ledger until the inventory close has been executed.

## Inventory aging report discrepancies

The **Inventory aging report** shows different values when viewed at different storage dimensions (such as site or warehouse). For more information about the reporting logic, see [Inventory aging report examples and logic](inventory-aging-report.md).
