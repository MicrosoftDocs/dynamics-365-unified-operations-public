---
# required metadata

title: Hide non-carrier delivery modes from POS shipment dialog
description: This topic explains a configuration option that can hide non-carrier modes of delivery from appearing in shipment configuration for POS.
author: hhainesms
manager: annbe
ms.date: 10/14/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hhainesms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.7

---

# Hide non-carrier delivery modes from shipping selection options in POS

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers a configuration option available for the point of sale (POS) application that changes the mode of delivery selection behavior when creating a shipment order in POS

During the creation of a customer order shipment from the POS, whether the user is choosing to ship the entire order or selected lines, the user is prompted to choose a mode of delivery for the shipment.

This mode of delivery selection screen by default shows all valid modes of delivery for the channel, item, and delivery address combination as defined in Retail Headquarters (HQ) on the **Sales and Marketing > Setup > Distribution > Modes of Delivery** page.   Pptions for “non-carrier” modes of delivery such as “carryout” or “pickup” may display here.

To provide an option to hide these "non-carrier" modes of delivery from this dialog, a parameter was added to the **Retail Parameters** page. From the **Customer Orders** tab on the **Retail Parameters** page, users may enable the **Show only carrier mode options for ship orders** setting. When this parameter is enabled, and after running the proper distribution jobs to sync this information to the Channel Database, the application will hide these "non-carrier" modes of delivery from the user display during the process of creating the shipment order in POS.
