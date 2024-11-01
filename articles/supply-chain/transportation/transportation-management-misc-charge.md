---
title: Transportation management miscellaneous charges
description: Learn how transportation-generated charges must be associated with a charge code and that you should have one setup for each relevant charges module setting.
author: lisascholz
ms.author: lisascholz
ms.topic: article
ms.date: 10/16/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: TMSMiscellaneousCharge
---

# Transportation management miscellaneous charges

[!include [banner](../includes/banner.md)]

As with all miscellaneous charges, transportation-generated charges must be associated with a charge code. Otherwise, they won't be added back to the order as a miscellaneous charge. The **Charges code** determines how the charge is accounted for in relation to the order and order line where it is added.

Go to **Transportation management > Setup > Rating > Miscellaneous charges** to define the qualifying criteria that determine when a specific **Charges code** is applied to a charge.

You should have at least one setup for each relevant **Charges module** setting (*Customer* and *Vendor*) where the **Miscellaneous charge type** is set to *None*. If this is missing, the miscellaneous charge will *not* be added to the order.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]