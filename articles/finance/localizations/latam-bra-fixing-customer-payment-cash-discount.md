---
# required metadata

title: Enable customer payments and cash discounts
description: This topic provides information about how to enable recalculation of cash discounts.
author: kfend
manager: AnnBe
ms.date: 10/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
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

When you create a Customer payment journal in a legal entity that is configured for Brazil, and the payment date grants cash discounts, if the date of payment in the payment journal is changed to another date where discounts are no longer applicable, the payment journal continues to calculate cash discounts.

Currently, the Customer payment journal does not remove the cash discount from the settlement amount when the payment date changes.This functionality changes the algorithm for calculatingf cash discounts to grant cash discounts within the proper range of the dates, according to the payment method setup. 

You can enable the Customer payment journal to recalculate the settlement amount and remove the cash discount if the payment date changes and it becomes out of date. To do this, go to **Feature management** and in the list, locate and enable the feature **Fixing the calculation of discount amount when the payment date changes**.


