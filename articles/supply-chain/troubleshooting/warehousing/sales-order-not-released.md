--- 
title: Sales order couldn't be released with outbound warehouse ops 
description: There are several reasons why you might receive an error message that a sales order could not be released. This page explains why and how to mitigate the issue. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
# Sales order could not be released with outbound warehouse operations

## Symptoms

When working with outbound warehouse operations, you may receive the following error message:

> Sales order could not be released.

## Cause

This issue can occur for several reasons. For example, the order is on credit management hold, and no shipments can be created until a valid postal address is entered for all sales lines that are associated with an order. Alternatively, there's an order hold that must be addressed before the order can be released to the warehouse. This hold might be order-specific, or it might be on the customer account.

## Resolution

Add or update the address on the sales order and order lines, and then release the order to the warehouse. Orders can be released to the warehouse only if they have a valid delivery address (per the address format setup in the **Organization administration** module).

Investigate the order hold and address the issues. Then remove the hold from the order or customer, and release the order to the warehouse.
