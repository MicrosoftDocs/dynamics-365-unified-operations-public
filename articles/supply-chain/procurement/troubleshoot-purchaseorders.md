---
# required metadata

title: Troubleshoot Purchase orders
description: This topic describes how to fix issues that you might encounter while working with Planning Optimization.
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
ms.dyn365.ops.version: AX 10.0.9

---
# Troubleshoot Purchase Orders 

This topic describes how to fix common issues that you might encounter while working with Planning Optimization.

## Unable to link a Purchase Agreement to a Purchase Order Line after creation

A purchase agreement has to be associated to the purchase order at the time of creation. Purchase order lines cannot be associated to purchase agreement lines if the purchase order was not initially associated at the time of purchase order creation.

This is by design.
## Unable to post more than one invoice for a purchase order line with category based items

Quantity is mandatory for posting invoices. So, if the full quantity on the line has been invoiced but only a partial amount and the expectation is to invoice the rest of the amount in another invoice, then that is not possible. 

This is by design.

## Changes to purchase orders are only allowed in state Draft when change management is activated

When you enable Planning Optimization, the built-in master planning engine is automatically disabled. Master planning batch jobs that were created for the built-in Supply Chain Management planning engine will fail if they are triggered while Planning Optimization is enabled. You may receive an error message such as *This operation triggered master planning that isn't supported when Planning Optimization is enabled*.

**Fix**: Cancel all master planning batch jobs that were created for the built-in Supply Chain Management planning engine.

## Updating Purchase Order in Received State creates Error

Planning Optimization differs from the built-in master planning design in some areas. This can also be caused by pending features.

**Fix**: Run Planning Optimization fit analysis and then analyze the results while referring to the related documentation to understand the impact. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Unable to edit the unit price for a purchase order line linked to an agreement

This is caused by a pending feature for Planning Optimization.

**Fix**: Until the pending feature is available, filter or delete planned orders to remove supply suggestions outside of the coverage time fence.

## What check triggers the prompt 'Update prices and discounts entered manually or external document' message?

We prompt this when changing the shipping date because often times this means that a different trade or sales agreement can get triggered, resulting in a price change. It can also effect warehouse schedules and other related information. It gets triggered whenever any of the dates have been changed, to ensure that the user is aware of price changes that can happen due to this change.

## Can I show only Purchase orders created by me?

This functionality is not available currently.


## Additional resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
