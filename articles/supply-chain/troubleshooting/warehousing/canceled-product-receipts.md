---
title: Canceled product receipts don't update transaction status to Registered
description: After you cancel product receipts on an inbound load, the system automatically updates the inventory transaction status from Received to Ordered.
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

# Canceled product receipts don't update transaction status to Registered

## Symptoms

After you run the **Cancel product receipts** action on an inbound load, the system automatically updates the status of inventory transactions from *Received* to *Ordered*.

## Resolution

When packing slips are canceled for outbound loads, the status of inventory transactions remains *Picked*. However, when product receipts from an inbound load are canceled, the status of inventory transactions isn't restored to *Registered*. Therefore, after a product receipt from an inbound load is canceled, the warehouse worker must re-register item quantities for the loads.

For more information, see [Register item quantities that arrive on an inbound load](/dynamics365/supply-chain/warehousing/inbound-load-handling#register-item-quantities-arriving).
