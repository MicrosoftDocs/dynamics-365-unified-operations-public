---
# required metadata

title: Items without inventory can be checked out
description: This topic provides troubleshooting guidance that can help when customers can add out-of-stock items to their cart and proceed to checkout.
author: Reza-Assadi
ms.date: 03/11/2021
ms.topic: Troubleshooting
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Items without inventory can be checked out

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when customers can add out-of-stock items to their cart and proceed to checkout.

## Description

Users can add an item to their cart, even though there is no on-hand inventory in the store, and then proceed to the checkout page.

## Resolution

### Enable the Show Out Of Stock Errors property in Commerce site builder

To enable the **Show Out Of Stock Errors** property in Commerce site builder, follow these steps.

1. Select the site that you're working on.
1. In the left navigation, select **Pages**.
1. Select **CartPage** to open it.
1. Select the **Cart 1** slot, select **Edit**, and then, in the properties pane, select the **Show Out Of Stock Errors** check box.
1. Save and publish the page.

## Additional resources

[Apply inventory settings](../inventory-settings.md)

[Calculate inventory availability for retail channels](../calculated-inventory-retail-channels.md)

[Configure inventory buffers and inventory levels](../inventory-buffers-levels.md)
