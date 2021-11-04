---
title: Canceled purchase orders appear in the draft list in the workspace
description: Canceled purchase orders appear in the draft list in the Purchase order preparation workspace
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Canceled purchase orders appear in the draft list in the workspace

## Symptoms

After you cancel purchase orders that were in a *Confirmed* state, the canceled purchase orders still appear in the list of draft purchase orders in the **Purchase order preparation** workspace.

## Resolution

This issue occurs only for purchase orders that are subject to change management. It occurs because the cancellation is considered a change that must be approved. The approval can be done automatically by the system. Therefore, the process is to submit the canceled purchase order to the approval workflow so that it can go to an *Approved* state. At that point, the purchase order will no longer appear in the list of draft purchase orders in the **Purchase order preparation** workspace.
