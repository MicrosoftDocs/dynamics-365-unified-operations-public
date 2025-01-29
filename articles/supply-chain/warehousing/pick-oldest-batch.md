---
title: Pick oldest batch on a mobile device
description: Learn how you set up and apply the options to pick the oldest batch from a mobile device with an outline on setting up the configuration for pick oldest batch.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:  WHSRFMenuItem
ms.topic: how-to
ms.date: 09/24/2024
ms.custom: 
  - bap-template
---

# Pick oldest batch on a mobile device

[!include [banner](../includes/banner.md)]

You can configure mobile device menu items to allow workers to pick any batch, or to force or warn them to pick the oldest batch in their current location. The option effects pick work for batch below items.

To set this option for a mobile device menu item, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Select or create a menu item that has **Use existing work** set to *Yes*.
1. On the **General** FastTab, set **Pick oldest batch** to one of the following values:
    - *None* – Workers aren't shown any messages and can pick any batch in their location.
    - *Warn* – When picking batch-controlled items, the app shows a list of the batch(es) with the oldest expiration date. If the location is license plate controlled, the app shows a list of license plates that have the oldest batch. If a worker chooses an unlisted license plate or batch, the app shows a warning that tells the worker that an older batch is available. The worker can choose to continue with the selected batch or license plate, even though it isn't the oldest, by confirming the action.
    - *Force* – Works the same way as a *Warn*, except the worker is only allowed to continue after selecting the oldest batch or license plate.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
