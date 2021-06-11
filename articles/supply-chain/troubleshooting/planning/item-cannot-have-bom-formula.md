---
title: Item can't have a BOM or formula
description: "When you are trying to firm an order, you get the following error during item validation: 'Item cannot have a BOM or formula'"
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPO
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Item can't have a BOM or formula

Error code: PRO2614

## Symptoms

When you are trying to firm an order, you get the following error during item validation:

> Item cannot have a BOM or formula

## Resolution

Items that have a bill of materials (BOM) or formula must be of type *Planning item*, *BOM*, or *formula*. To change the type of an item:

1. Go to **Product information management > Products > Released products**
1. Open the relevant product.
1. Expand the **Engineer** FastTab.
1. Set **Production type** to *Planning item*, *BOM*, or *formula*.
