---
# required metadata

title: not able to invoice the customer-facing sales order in the VEL company
description: not able to invoice the customer-facing sales order in the VEL company
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesEditLines
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# not able to invoice the customer-facing sales order in the VEL company

KB Number: 4611793

Customer not able to invoice the original sales order and the original direct delivery purchase order after set the "Post invoice automatically" parameters 


## Resolution
The intercompany and direct delivery orders invoice sync behavior is controller and forced by the parameters in  
https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-parameters-to-post-an-intercompany-order. 
Once these parameters are set, customer will have to invoice the Intercompany sales order first, and only after that the original sales and purchase orders will be synced to invoiced. 


