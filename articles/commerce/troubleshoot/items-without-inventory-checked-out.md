---
# required metadata

title: Items without inventory can be checked out
description: This topic provides troubleshooting for when customers can add items without on-hand inventory to the cart and proceed to check out. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/23/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
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

This topic provides troubleshooting for when customers can add items without on-hand inventory to the cart and proceed to the checkout page.

## Description

A user is able to add an item without on-hand inventory in the store to their cart and proceed to the checkout page.

## Resolution

### Enable the "Show Out Of Stock Errors" property in Commerce site builder

To enable **Show Out Of Stock Errors** in Commerce site builder, follow these steps.

1. Select the site you're working on.
1. Select **Pages** in the left navigation.
1. Select the **CartPage** to open it.
1. Select the **Cart 1** slot, select **Edit**, and then select the **Show Out Of Stock Errors** check box in the properties pane.
1. Save and publish the page.

## Additional resources

[Apply inventory settings](../inventory-settings.md)

[Calculate inventory availability for retail channels](../calculated-inventory-retail-channels.md)

[Configure inventory buffers and inventory levels](../inventory-buffers-levels.md)
