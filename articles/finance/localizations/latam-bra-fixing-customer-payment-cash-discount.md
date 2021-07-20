---
# required metadata

title: Enable customer payments and cash discounts
description: This topic explains how to enable recalculation of cash discounts.
author: kfend
ms.date: 10/16/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 270254
ms.assetid: 92223189-69a8-4a40-b867-ef9b4f14c23d
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2019-10-07
ms.dyn365.ops.version: 10.0.5

---

# Enable customer payments and cash discounts

[!include [banner](../includes/banner.md)]

When you create a Customer payment journal in a legal entity that is configured for Brazil, and cash discounts are applicable on the payment date, if you change the payment date in the payment journal to a date when discounts are no longer applicable, the payment journal currently continues to calculate cash discounts. It doesn't remove the cash discounts from the settlement amount.

The "Fixing the calculation of discount amount when the payment date changes" feature changes the algorithm for calculating cash discounts, so that cash discounts are given in the correct range of the dates, according to the setup of the payment method. When you turn on this feature, the Customer payment journal recalculates the settlement amount and removes cash discounts if the payment date changes and becomes out of date. To use this feature, go to **Feature management**, find the **Fixing the calculation of discount amount when the payment date changes** feature in the list, and turn it on.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]