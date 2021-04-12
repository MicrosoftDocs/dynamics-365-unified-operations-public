---
title: not able to invoice the customer-facing sales order in the VEL company
description: not able to invoice the customer-facing sales order in the VEL company
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: SalesEditLines
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# not able to invoice the customer-facing sales order in the VEL company

KB Number: 4611793

Customer not able to invoice the original sales order and the original direct delivery purchase order after set the "Post invoice automatically" parameters 


## Resolution
The intercompany and direct delivery orders invoice sync behavior is controller and forced by the parameters in  
https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-parameters-to-post-an-intercompany-order. 
Once these parameters are set, customer will have to invoice the Intercompany sales order first, and only after that the original sales and purchase orders will be synced to invoiced. 


