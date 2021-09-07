---
title: Cancelling delivery remainder moves purchase order to a Confirmed state
description: If a delivery remainder is canceled on a purchase order where change management is turned on, the purchase order goes to a Confirmed state
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

# Cancelling delivery remainder moves purchase order to a Confirmed state

## Symptoms

For a purchase order that is subject to change management, if the only change that is requested is the cancellation of a delivery remainder on one or more of the lines, the purchase order will go directly to a *Confirmed* state when it's approved, and no journal will be created.

## Resolution

Cancellation of a delivery remainder doesn't affect the contents of the confirmation journal. This functionality should be used when the line has been partially received, and the remainder quality should be canceled in the process step after the purchase order has been confirmed with the vendor.

If this should be reflected on the purchase order confirmation, the quantity should be adjusted on the purchase order line so that the confirmation will be required. Alternatively, if nothing has been received on the line, the quantity can be removed. In this case, reconfirmation will be required.
