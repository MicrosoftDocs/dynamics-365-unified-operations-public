---
# required metadata

title: Items without inventory can be checked out
description: This topic provides troubleshooting for when a customer can add an item without on-hand inventory to their cart and check out. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
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

## Description
A user is able to add an item that has no on-hand inventory in the store to their cart and proceed to the checkout page.

## Resolution

### Enable "Show Out Of Stock Errors" on the "CartPage" page

1. Go to site builder.
 
1. Select the site you're working on.
 
1. Select **Pages** in the left navigation.

1. Select **CartPage**.

1. Select the **Cart 1** module on the left, select **Edit**, and then select the **Show Out Of Stock Errors** checkbox.

1. Save and publish the page.

## Additional Resources
- [Apply inventory settings in e-Commerce site settings](../inventory-settings.md)
- [Calculate inventory availability for retail channels](../calculated-inventory-retail-channels.md)
- [Configure inventory buffers and inventory levels](../inventory-buffers-levels.md)






