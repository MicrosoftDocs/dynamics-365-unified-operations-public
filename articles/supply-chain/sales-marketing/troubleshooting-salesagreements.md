---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Sales Quotations.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesAgreement, PurchAgreement
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
# Troubleshoot Sales Quotations 

This topic describes how to fix common issues that you might encounter while working with Sales Orders.

##  Changing the location in a sales order header does not update the tax information 
If site or warehouse or delivery address is being changed on a sales order header or at the line level, the case tax information is not getting updated for the lines automatically.
		
**Resolution/Fix**
That's because the delivery address, site and warehouse doesn't automatically get changed at the line level either - you'll need to update that yourself


## Additional resources

[Get started with Sales Orders](get-started.md)

