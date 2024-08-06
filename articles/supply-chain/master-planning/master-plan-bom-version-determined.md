---
title: Determine the BOM version
description: During a demand explosion, if an item has a default order type of Production, the planning engine finds a valid BOM version based on the site. 
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
audience: Application User 
ms.search.form: BOMConsistOf, BOMDesigner, InventItemOrderSetup
ms.assetid: a5b64301-a011-4469-afaf-e4c9164ef9c6
---

# Determine the BOM version

[!include [banner](../includes/banner.md)]

During a demand explosion, if an item has a default order type of Production, the planning engine finds a valid BOM version based on the site. 

The site dimension is always known and is stated on the demand transaction. The following process is used to determine the BOM version to use:

-   If there is a BOM version defined for the item at the demand site, the site-specific BOM is used.
-   If there is no site-specific BOM version defined for an item at the demand site, a general BOM is used. A general BOM does not state a site, and it is valid for multiple sites. If there is a general BOM, it is used.
-   If there is no general BOM version to use, the demand explosion stops at this point.

A valid BOM version, whether site-specific or general, must meet the required criteria for date and quantity.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]