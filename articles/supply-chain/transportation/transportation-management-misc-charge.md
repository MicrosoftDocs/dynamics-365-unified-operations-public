---
# required metadata

title: Transportation management miscellaneous charges
description: This topic explains how transportation-generated charges must be associated with a charge code.
author: Henrikan
manager: tfehr
ms.date: 10/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: henrikan
ms.search.validFrom: 2020-10-16
ms.dyn365.ops.version: Release 10.0.14
---

# Transportation management miscellaneous charges

[!include [banner](../includes/banner.md)]

As with all miscellaneous charges, transportation-generated charges must be associated with a charge code. Otherwise, they won't be added back to the order as a miscellaneous charge. The **Charges code** determines how the charge is accounted for in relation to the order and order line where it is added.

Go to **Transportation management > Setup > Rating > Miscellaneous charges** to define the qualifying criteria that determine when a specific **Charges code** is applied to a charge.

You should have at least one setup for each relevant **Charges module** setting (*Customer* and *Vendor*) where the **Miscellaneous charge type** is set to *None*. If this is missing, the miscellaneous charge will *not* be added to the order.
