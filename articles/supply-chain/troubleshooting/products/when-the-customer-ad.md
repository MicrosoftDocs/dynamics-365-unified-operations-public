---
title: When the customer adds text transactions, product name on the PO is still original text.
description: When the customer adds text transactions, product name on the PO is still original text.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: EcoResProductDetailsExtended, SysTranslationDetail
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# When the customer adds text transactions, product name on the PO is still original text.

KB Number: 4612098

## Issue description

The customer added text transactions and created PO, then changed language. Product name on the PO is still original text.
The customer struggles with their employees who works at overseas branch can’t check a product order.

## Resolution

Unfortunately, this is by design. Product translations are only supported on external facing documents as described in https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/translations-product-related-information#where-can-i-view-the-translated-information
