---
# required metadata

title: Unable to post packing slip for a stopped a sales order line
description: Unable to post packing slip for a stopped a sales order line
author: mfp@microsoft.com
manager: tfehr
ms.date: 2/18/2022 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: mfp@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: mfp@microsoft.com

---

# Unable to post packing slip for a stopped a sales order line

Error code: SYS13203

The system displays the followign error message:
	SYS13203

Unable to post packing slip when stopping a sales order line after confirming the outbound shipment

## Symptoms
The system shows the following error message: > A quantity cannot be picked.

## Cause
When marking a sales order line as Stopped, the system will prevent further processing of the sales order, in this case the posting of the packing slip. 
In the scenario where the outbound shipment has been confirmed, the shipment containing the sales order has already physically left the warehouse, and it is no longer possible to physically stop shipment of the sales order.

## Resolution
To allow posting the packing slip, set the Stopped flag on the sales order lines to No.



