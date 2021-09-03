---
title: Update conflict when inventory valuation method is standard cost or moving average
description: An update conflict occurs when the inventory valuation method is either standard cost or moving average
author: AndersGirke
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails, InventValueProcess, InventValueReportSetup, InventClosing
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.15
---

# An update conflict occurs when the inventory valuation method is either standard cost or moving average

## Symptoms

When you post documents such as inventory journals, purchase order invoices, or sales order invoices in parallel for scalability and performance, you might receive an error message about an update conflict, and some of the documents might not be posted. This issue can occur when the inventory valuation method is either *Standard cost* or *Moving average*. Both these methods are perpetual costing methods. In other words, the final cost is determined at the time of posting.

If you're using the *Moving average* method, the error message resembles this example:

> Inventory value xx.xx is not expected after the proportional expense calculation

If you're using the *Standard cost* method, the error message resembles this example:

> The standard cost does not match with the financial inventory value after the update. Value = xx.xx, Qty = yy.yy, Standard cost = zz.zz

## Workaround

Until Microsoft releases a solution to fix the issue, consider using the following workarounds to help avoid or reduce these errors:

- Repost the failed documents.
- Create documents that have fewer lines.
- Avoid decimal values in the standard cost. Try to define the standard cost so that the **Price quantity** field is set to *1*. If you must specify a **Price quantity** value that is more than *1*, try to minimize the number of decimal places in the unit standard cost. (Ideally, there should be fewer than two decimal places.) For example, avoid defining standard cost settings such as **Price** = *10* and **Price quantity** = *3*, because they will produce a unit standard cost of 3.333333 (where the decimal value repeats).
- In a majority of documents, avoid having multiple lines that hold the same combination of product and financial inventory dimensions.
- Reduce the degree of parallelization. (In this case, your system might become faster, because fewer update conflicts and retries occur.)
