---
# required metadata

title: When the customer adds text transactions, product name on the PO is still original text.
description: When the customer adds text transactions, product name on the PO is still original text.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDetailsExtended, SysTranslationDetail
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: benebotg@microsoft.com

---

# When the customer adds text transactions, product name on the PO is still original text.

KB Number: 4612098

The customer added text transactions and created PO, then changed language. Product name on the PO is still original text.
The customer struggles with their employees who works at overseas branch can’t check a product order.



## Resolution
Unfortunately, this is by design. Product translations are only supported on external facing documents as described in https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/translations-product-related-information#where-can-i-view-the-translated-information



