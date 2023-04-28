--- 
# required metadata 
 
title: Create a purchase order for a one-time supplier
description: This procedure shows you how to create a purchase order for a one-time supplier. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase order for a one-time supplier

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase order for a one-time supplier. The supplier is created automatically with the purchase order, rather than having to create the vendor account manually. Purchase orders are typically created by a purchasing agent. The example shown in this guide can be used in the USMF demo data company. It is a prerequisite that a one-time vendor account has been set up in the Account payable parameters page.


## Create a purchase order for a one-time supplier
1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
2. Click New.
3. Select Yes in the One-time supplier field.
    * A vendor account is automatically created and assigned to the purchase order. The vendor account is created based on the template that is specified on the General tab in the Accounts payable parameters page.  
4. In the Name field, type a name for the supplier.
5. Click OK.
    * The purchase order can now be completed and processed like any other order. There are no special characteristics related to how this is done. The invoice will account a due transaction on the vendor account that was created with the order, and payment will then be processed.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]