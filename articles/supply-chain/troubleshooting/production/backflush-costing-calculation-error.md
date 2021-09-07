--- 
title: Backflush costing calculation error during inventory closing 
description: In earlier releases, you may have received a Backflush costing calculation error during inventory closing. This issue has been fixed. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Backflush costing calculation error during inventory closing

## Symptoms

In releases before release 10.0.13, if you aren't using the lean production costing flow, you receive the following erroneous warning message during inventory closing:

> You are about to execute an Inventory close with a date %1. No execution of Backflush costing calculation with a date %1 matching period end has been registered. Please remember to execute a Backflush costing calculation with a date of %1 matching period end. The valuation of inventories, cost of goods sold, and variances might not be correct in Subledger or General ledger until this has been executed.

## Resolution

This issue has been fixed in release 10.0.13 and later. For more information, see [KB 4582468](https://fix.lcs.dynamics.com/Issue/Details?kb=4582468&bugId=468844&dbType=3&qc=fcd64080446a27382cfde3e4c3bdcfb714279185932259cd11ceb0d500617296).
