---
# required metadata

title: Pass returned items on to inspection 
description: When registering a returned item, determine that an item should be sent for inspection before it's returned to inventory or disposed of in some other way.
author: Henrikan
ms.author: henrikan
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WMSJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Pass returned items on to inspection

[!include [banner](../includes/banner.md)]

When registering a returned item, you may determine that an item should be sent for inspection before it's returned to inventory or disposed of in some other way.

1. Go to **Inventory management** \> **Journals** \> **Item arrival** \> **Item arrival**.

    \-or-

    Go to **Inventory management** \> **Journals** \> **Item arrival** \> **Production input**.

1. On the **Location journal** form, register the receipt of an item as usual.

    > [!NOTE]
    > For information about registering the receipt of returned items, see [Register the receipt of returned items](register-the-receipt-of-returned-items.md)

1. On the **Default values** tab, in the **Mode of handling** area, select the **Quarantine management** box.

This prompts the system to create a quarantine order, and the person or department that performs inspections respond to this order using the **Quarantine order** form.

## See also

- [Take returned items through inspection](take-returned-items-through-inspection.md)
- [Specify how to dispose of returned items](specify-how-to-dispose-of-returned-items.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]