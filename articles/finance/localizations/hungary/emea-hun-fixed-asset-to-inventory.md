---
title: Move a fixed asset to inventory
description: Learn about country/region-specific functionality for Hungary that lets you transfer fixed assets to inventory at the net book value.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Hungary
ms.search.validFrom: 2016-11-30
ms.search.form: InventJournalAsset
---

# Move a fixed asset to inventory

[!include [banner](../../includes/banner.md)]

This article describes country/region-specific functionality for Hungary that lets you transfer fixed assets to inventory at the net book value. The status of the fixed asset is set to **Scrapped**, and the net book value is set to 0. Additionally, the quantity of a product in inventory is set to 1, and the cost price is set to the net book value of the fixed asset.

Use the standard **Inventory to fixed assets** journal to transfer fixed assets to inventory.

To transfer a fixed asset to inventory, follow these steps:

1. Validate that the depreciation for the fixed asset is posted up to the transfer date.
1. Create a new **Inventory to fixed assets** journal.
1. On the journal lines, select the asset to transfer and the product to receive.
1. Enter a negative quantity.
1. Validate that the **Cost price** field has the **Net book** value.
1. Post the journal.
1. Validate that the fixed asset and inventory transactions were created correctly.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
