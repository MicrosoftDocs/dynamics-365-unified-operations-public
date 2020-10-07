---
# required metadata

title: Troubleshoot Process Manufacturing
description: This topic describes how to fix issues that you might encounter while working with Process Manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
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
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Process Manufacturing

This topic describes how to fix common issues that you might encounter while working with Process Manufacturing.

## When reporting a partial quantity on a job on the job card device, and the job is the last job for the production order, then all previous jobs on the production order that are in status *In progress* will be automatically ended.

This is working by design. In the production defaults parameters, there is a parameter called 'End-mark route' under the 'Report as Finished' tab. When this parameter is selected, a route card journal is posted when reporting on the last operation on the job card device or job card terminal. This journal is marking all the operations as completed and ending all the production jobs. The End-mark route parameter will not consider the desired job status the user is selecting when reporting on the last operation. The system will also not consider if the user is reporting a full or partial quantity.

## When attempting a stock closing a warning occurs stating "No execution of backflush costing calculation with a date of xxx has been registered". When lean manufacturing is not user, this message should not appear.
This issue has been fixed from 10.0.13 and onwards. See more here: KB 4582468.

**Issue description:**
Before 10.0.13, when not using lean production costing flow, a warning message is still displayed during inventory closing "You are about to execute an Inventory close with a date X. No execution of Backflush costing calculation with a date X matching period end has been registered. Please remember to execute a Backflush costing calculation with a date of X matching period end. The valuation of inventories, cost of goods sold and variances may not be correct in Subledger or General ledger until this has been executed.", which is a bug.

