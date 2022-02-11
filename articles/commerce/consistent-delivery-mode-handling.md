---
# required metadata

title: Enable consistent delivery mode handling in e-Commerce channel
description: This topic explains possible issues around charges flow in e-Commerce channel in Microsoft Dynamics 365 Commerce, and feature switch to handle the issues.
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 02/10/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
ms.dyn365.ops.version: 10.0.26
---

# Display non-prorated header level charges 

If you are experiencing one of the following issues in e-Commerce channel, turn on **Enable consistent delivery mode handling in channel** feature

1. In E-Commerce channel, non-prorated header level charges will not appear.
2. In E-Commerce channel, charges for delivery modes will be not consistent between mode of delivery selection and order summary in the checkout. 


In Dynamics 365 Commerce, by default non-prorated header level charges are not applied in e-Commerce channel. To see header level non-prorated charges in the e-Commerce channel, make sure that **Enable consistent delivery mode handling in channel** feature is enabled under ** Feature management > all **

Note that **Enable consistent delivery mode handling in channel** feature also ensures that deliver information of a sales order is handled by the same request workflow and handled consistently. 
