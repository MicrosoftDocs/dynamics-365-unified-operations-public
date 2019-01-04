---
# required metadata

title: Omni-Channel Advanced Auto Charges
description: This topic describes capabilities for managing additional order charges for Retail channel orders using Advanced Auto Charges features.
author: hhaines
manager: AnnBe
ms.date: 1/4/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: , 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16231
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Omni-Channel Advanced Auto Charges

[!include [banner](includes/banner.md)]

This topic will provide information on configuration and deployment of the Advanced Auto Charges feature.

By enabling the Advanced Auto Charges features in Dynamics 365 for Commerce, orders created in any supported Retail channel (POS, Call Center and Online), will be able to take advantage of the Auto-Charges configurations defined in the backoffice application at both the header and line level.   

In previous releases, the auto-charges configurations were only accessible by orders created in Ecommerce and Call Center channels.  With this feature change, POS created orders will now be able to leverage the auto-charges configurations, if defined, and have additional misc charges calculated and added to these sales transactions.

Before the release of the Advanced Auto Charges feature, a POS user was only prompted to manually enter a shipping fee during the creation of a "ship all" or "ship selected" POS transaction.   While this feature utilized the misc charges capabilities of the application in respect to how the charges were written to the order, it did not provide a systematic calculation and relied on the user's input to determine the value of the charges.  These charges were also only able to be added as a single "shipping" related charges code and could not easily be edited or changed in the POS once created. With the new Advanced Auto Charges feature, POS users will now be able to have systematic calculations for any defined misc charges code based on auto-charges setup tables.  In addition, users will have the ability to add or edit an unlimited amount of additional charges/fees to any POS sales transaction at the header or line level (cash and carry or customer order).


