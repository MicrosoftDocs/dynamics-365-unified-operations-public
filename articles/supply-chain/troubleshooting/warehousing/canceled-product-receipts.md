---
title: Canceled product receipts don't update transactions status to registered
description: After you cancel product receipts on an inbound load, the system automatically updates the inventory transaction status from Received to Ordered
author: GalynaFedorova
ms.date: 06/11/2021
ms.topic: troubleshooting
ms.search.form: WMSPickingRegistration
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-11
ms.dyn365.ops.version: 10.0.20
---

# Canceled product receipts don't update transactions status to registered

## Symptoms

After you run **Cancel product receipts** on an inbound load, the system automatically updates the inventory transaction status from *Received* to *Ordered*.

## Resolution

Unlike packing slip cancellations for outbound loads, where inventory transactions retain in the status *Picked*, cancelling a product receipt from an inbound load doesn't restore the inventory transactions to the status of *Registered*. Therefore, after cancelling a product receipt from the inbound load, the warehouse worker must re-register items quantities for the loads.

For more information, see [Register item quantities that arrive on an inbound load](/dynamics365/supply-chain/warehousing/inbound-load-handling#register-item-quantities-arriving).
