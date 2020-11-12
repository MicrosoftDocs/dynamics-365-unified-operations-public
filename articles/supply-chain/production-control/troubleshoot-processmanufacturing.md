---
# required metadata

title: Troubleshoot process manufacturing
description: This topic describes how to fix issues that you might encounter while you work with process manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 11/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.author: smnatara
ms.search.validFrom: 2020-11-04
ms.dyn365.ops.version: 10.0.15

---
# Troubleshoot process manufacturing

This topic describes how to fix issues that you might encounter while you work with process manufacturing.

## When I use the job card device to report a partial quantity on the last job in a production order, all the previous jobs on that order that have a status of In progress are automatically ended.

This behavior is by design. On the **Production order defaults** page, on the **Report as finished** tab, there is an option that is named **End-mark route**. If this topic is set to *Yes*, a route card journal is posted when a worker uses the job card device or job card terminal to report the last operation. This journal marks all the operations as completed and ends all the production jobs. When the **End-mark route** option is set to *Yes*, the system doesn't consider the job status that the worker selected when they reported the last operation. The system also doesn't consider whether the worker is reporting a full or partial quantity.

## When I attempt a stock closing, I receive the following warning message: "No execution of Backflush costing calculation with a date %1 matching period end has been registered."

In releases before release 10.0.13, if you aren't using the lean production costing flow, you receive the following erroneous warning message during inventory closing:

> You are about to execute an Inventory close with a date %1. No execution of Backflush costing calculation with a date %1 matching period end has been registered. Please remember to execute a Backflush costing calculation with a date of %1 matching period end. The valuation of inventories, cost of goods sold and variances might not be correct in Subledger or General ledger until this has been executed.

This issue has been fixed in release 10.0.13 and later. For more information, see KB 4582468.
