---
# required metadata

title: Troubleshoot process manufacturing
description: This topic describes how to fix issues that you might encounter while working with Process Manufacturing.
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

This topic describes how to fix common issues that you might encounter while working with process manufacturing.

## When I use the job card device to report a partial quantity on the last job in a production order, then all the previous jobs with a status of "In progress" on that order are automatically ended.

This is by design. On the **Production order defaults** page, there is a setting called **End-mark route** on the **Report as finished** tab. When **End-mark route** is set to *Yes*, a route card journal is posted when a worker reports the last operation using the job card device or job card terminal. This journal marks all the operations as completed and ends all the production jobs. The **End-mark route** setting won't consider the desired job status selected by the worker when reporting on the last operation. The system also won't consider whether the worker is reporting a full or partial quantity.

## When I attempt a stock closing, I see the warning "No execution of backflush costing calculation with a date of %1 has been registered."

This issue has been fixed in release 10.0.13 and onwards. See more here: KB 4582468.

Before release 10.0.13, when you aren't using lean production costing flow, the following erroneous warning message was displayed during inventory closing: "You are about to execute an Inventory close with a date %1. No execution of Backflush costing calculation with a date %1 matching period end has been registered. Please remember to execute a Backflush costing calculation with a date of %1 matching period end. The valuation of inventories, cost of goods sold and variances may not be correct in Subledger or General ledger until this has been executed."

