---
title: The purchase agreement maximum limit isn't effective on a purchase requisition
description: The purchase agreement maximum limit isn't effective on a purchase requisition
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart, PurchRFQTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# The purchase agreement maximum limit isn't effective on a purchase requisition

## Symptoms

When a purchase requisition is linked to a purchase agreement, the maximum limit from the purchase agreement isn't effective on the purchase requisition. The default price information is correctly entered, but more than the maximum limit from the purchase agreement can be ordered in the purchase requisition.

## Resolution

This behavior is expected. Because requisitions aren't always approved, a quantity or amount should not be reserved on the purchase agreement. Therefore, you won't meet the maximum limit from the purchase agreement.
