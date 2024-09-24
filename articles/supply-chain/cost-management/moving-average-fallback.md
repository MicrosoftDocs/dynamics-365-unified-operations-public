---
title: Moving average fallback cost sequence
description: Learn about fallback cost sequences for moving average calculations in Microsoft Dynamics 365 Supply Chain Management with a step-by-step process.
author: JennySong-SH
ms.author: yanansong
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: MM/DD/YYYY
ms.date: 09/24/2024
  - bap-template
---

# Moving average fallback cost sequence

[!include [banner](../includes/banner.md)]

One way that you can calculate the cost of your inventory is by using a *moving average*. Up to three cost values can be associated with each inventory item:

- **Last issue** – The last issue cost that was assigned before inventory went negative
- **Active cost** – The latest cost that was activated in a costing version
- **Item price** – The cost that is specified for the released product

To determine which of these cost values should be used in moving average calculations, the system uses a *fallback cost sequence* to establish the order of preference for the values. If the preferred cost value isn't available, the system uses the next-preferred value, and so on.

To select the fallback cost sequence for moving average calculations, follow these steps.

1. Go to **Cost management** \> **Inventory accounting policies setup** \> **Parameters**.
2. On the **Inventory accounting** tab, in the **Moving average** section, set the **Fallback cost sequence** field to one of the following values:

    - *Last issue – Active cost – Item price* – This is the default sequence.
    - *Active cost – Last issue*
    - *Active cost – Item price* – Organizations might experience performance issues if they use business processes where inventory regularly goes negative and, at the same time, the transaction volume is high. This setting can help mitigate those performance issues.

![Inventory accounting parameters.](media/inventory-accounting-parameters.png "Inventory accounting parameters")

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
