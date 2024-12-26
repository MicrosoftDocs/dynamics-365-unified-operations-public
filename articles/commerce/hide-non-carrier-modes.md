---
title: Hide non-carrier delivery modes from the shipment options in POS
description: This article describes a configuration option that can prevent non-carrier modes of delivery from appearing for selection when shipment orders are created in the point of sale (POS) application.
author: hhainesms
ms.date: 10/24/2019
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Hide non-carrier delivery modes from the shipping options in POS


[!include [banner](includes/banner.md)]

This article describes a configuration option that is available for the point of sale (POS) application. This configuration option changes the behavior for the selection of a mode of delivery when shipment orders are created in POS.

When users create customer shipment orders in POS, they can select a mode of delivery for the shipment. This functionality is available regardless of whether the whole order is being shipped or only selected lines.

By default, the dialog box where a mode of delivery is selected shows all the valid modes of delivery for the combination of a channel, an item, and a delivery address. These modes of delivery are defined on the **Modes of delivery** page in Headquarters (**Sales and marketing \> Setup \> Distribution \> Modes of delivery**). "Non-carrier" modes of delivery, such as **Carryout** or **Pickup**, might also appear for selection in the dialog box.

However, a feature has been added that lets you hide non-carrier modes of delivery in the dialog box. To turn on this feature, on the **Commerce parameters** page, on the **Customer orders** tab, set the **Show only carrier mode options for ship orders** option to **Yes**. After you turn on this feature and run the appropriate distribution jobs to sync the information to the channel database, non-carrier modes of delivery won't appear for selection during the process of creating shipment orders in POS.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
