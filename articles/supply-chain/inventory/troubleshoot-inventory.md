---
# required metadata

title: Troubleshoot Purchase orders
description: This topic describes how to fix issues that you might encounter while working with Purchase Orders.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
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
# Troubleshoot Inventory Management 

This topic describes how to fix common issues that you might encounter while working with inventory management.

## Unable to see transactions from a Quality Order
	When you try to look at the transactions directly from a Quality Order, the system shows you nothing. The same behavior can be seen for any orders Inventory, Sales, Purchase, Production orders.
	
**Repro steps**
 1. Create a Quality Order
 2. Validate the Order
 3. Go to Inventory management > Periodic tasks > Quality management > Quality orders > Inventory > Transactions
 
 **Results**
 No transactions are shown.
 
 **Resolution/Fix**
 The transactions can be seen from the Inventory blocking view. It is not currently possible to view inventory blocking transactions from the quality order view.

## Additional resources

[Get started with Inventory Management](get-started.md)
