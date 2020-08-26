---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Sales Orders.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesTable, SalesTableListPage
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
# Troubleshoot Sales Orders 

This topic describes how to fix common issues that you might encounter while working with Sales Orders.

##  Changing the location in a sales order header does not update the tax information 
If site or warehouse or delivery address is being changed on a sales order header or at the line level, the case tax information is not getting updated for the lines automatically.
		
**Resolution/Fix**
That's because the delivery address, site and warehouse doesn't automatically get changed at the line level either - you'll need to update that yourself

##  When there are two trade agreements for the same/overlapping period, then the same agreement line is always picked.
If there are two trade agreements defined for the same/overlapping period, then when creating sales order lines with those items, the sam etrade agreement seems to be picked each time.
		
**Resolution/Fix**
When there is more than one trade agreement for a given date, then the trade agreement with the lower price will always be picked up. Read more on trade agreements [here] (https://www.axug.com/HigherLogic/System/DownloadDocumentFile.ashx?DocumentFileKey=3396a3a8-1f48-4d85-8cd6-5fa982f62e90).


## Additional resources

[Get started with Sales Orders](get-started.md)

