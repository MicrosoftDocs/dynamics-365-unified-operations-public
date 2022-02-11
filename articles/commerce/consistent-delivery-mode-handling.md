---
# required metadata

title: Enable consistent delivery mode handling in e-Commerce channel
description: This topic explains possible issues around charges flow in e-Commerce channel in Microsoft Dynamics 365 Commerce, and feature switch to handle the issues.
author: gvrmohanreddy
ms.date: 02/10/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Display non-prorated header level charges 

If you are experiencing one of the following issues in e-Commerce channel, turn on **Enable consistent delivery mode handling in channel** feature

1. In E-Commerce channel, non-prorated header level charges will not appear.
2. In E-Commerce channel, charges for delivery modes will be not consistent between mode of delivery selection and order summary in the checkout. 


In Dynamics 365 Commerce, by default non-prorated header level charges are not applied in e-Commerce channel. To see header level non-prorated charges in the e-Commerce channel, make sure that **Enable consistent delivery mode handling in channel** feature is enabled under ** Feature management > all **

Note that **Enable consistent delivery mode handling in channel** feature also ensures that deliver information of a sales order is handled by the same request workflow and handled consistently. 
