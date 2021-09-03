---
title: Purchase orders don't reflect the language settings of the legal entity
description: The product name on a purchase order is shown in the system language instead of the language set for the legal entity where the purchase order was created
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

# Purchase orders don't reflect the language settings of the legal entity


## Symptoms

The product name on a purchase order is shown in the system language instead of the language that is set for the legal entity where the purchase order was created.

## Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Set the system language to *EN-US* (US English).
1. Make sure that there is a product where the *EN-US* and *DE* (German) languages are maintained for translations of the product name.
1. Change the language of a legal entity to *DE*.
1. In the legal entity where *DE* is set as the language, create a purchase order that includes the product.
1. Notice that the product name is still shown in US English (the system language).

## Resolution

This behavior is by design. On purchase orders, the product is always shown in the system language. The purchase order language is used when a confirmation journal is created.
