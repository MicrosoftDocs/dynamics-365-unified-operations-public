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
<!-- KFM: This topic is not clear. Please revise and rephrase for a general audience (not a specific customer). What is "the VEL company"? -->
# Can't invoice a customer-facing sales order in the VEL company

KB Number: 4611793

## Issue description

Customer not able to invoice the original sales order and the original direct delivery purchase order after set the "Post invoice automatically" parameters

## Resolution

The intercompany and direct delivery orders invoice sync behavior is controller and forced by the parameters described in [Set up parameters to post an intercompany order](/dynamicsax-2012/appuser-itpro/set-up-parameters-to-post-an-intercompany-order).

Once you have set these parameters, you must invoice the intercompany sales order first. After that, the original sales and purchase orders will be synced to invoiced.
