--- 
# required metadata 
 
title: Create a purchase order for a one-time supplier
description: This procedure shows you how to create a purchase order for a one-time supplier. 
author: FrankDahl
manager: AnnBe 
ms.date: 08/23/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase order for a one-time supplier

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to create a purchase order for a one-time supplier. The supplier is created automatically with the purchase order, rather than having to create the vendor account manually. Purchase orders are typically created by a purchasing agent. The example shown in this guide can be used in the USMF demo data company. It is a prerequisite that a one-time vendor account has been set up in the Account payable parameters page.


## Create a purchase order for a one-time supplier
1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
2. Click New.
3. Select Yes in the One-time supplier field.
    * A vendor account is automatically created and assigned to the purchase order. The vendor account is created based on the template that is specified on the General tab in the Accounts payable parameters page.  
4. In the Name field, type a name for the supplier.
5. Click OK.
    * The purchase order can now be completed and processed like any other order. There are no special characteristics related to how this is done. The invoice will account a due transaction on the vendor account that was created with the order, and payment will then be processed. When this is completed, the vendor account can be deleted. This is typically done by the accounts payable department.  

