---
title: Can't invoice a customer-facing sales order
description: You can no longer invoice the original sales order and the original direct delivery purchase order after setting the Post invoice automatically parameters.
author: niwang
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

# Can't invoice a customer-facing sales order

KB Number: 4611793

## Symptoms

You can no longer invoice the original sales order and the original direct delivery purchase order after enabling the **Post invoice automatically** option on the **Intercompany** settings page for a vendor.

## Resolution

The intercompany and direct delivery order invoice sync behavior is controller and forced by the parameters described in [Set up parameters to post an intercompany order](/dynamicsax-2012/appuser-itpro/set-up-parameters-to-post-an-intercompany-order).

Once you have set these parameters, you must invoice the intercompany sales order first. After that, the original sales and purchase orders will be synced to invoiced.
