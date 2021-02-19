---
# required metadata

title: Pickup in store option doesn't display
description: This topic provides troubleshooting for when the option to pickup in store doesn't display in the shopping bag or product details page. 
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

# Pickup in store option doesn't display

[!include [banner](../../includes/banner.md)]

## Description
When navigating to the **Product details** or the **Shopping cart** page, the **Pick this up** button does not show up for a product.

## Resolution

### Enable "BOPIS" extension in site builder

1. Go to site builder

1. On the **Sites** page, select the site you're working on.

1. Expand **Site settings** on the bottom left of the navigation pane, and then select **Extensions**.

1. Make sure the **Disable BOPIS** option is unselected.

### Configure modes of delivery

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Retail and Commerce > Channel setup > Modes of delivery**.

1. Make sure a **Customer pickup** mode of delivery was created, and **Products* and **Addresses** are assigned to it.

1. Go to **Retail and Commerce > Headquarters setup > Parameters**.

1. Select the **Customer orders** tab on the left panel.

1. Make sure the **Pickup mode of delivery** is configured correctly.

### Configure customer orders payments

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Retail and Commerce > Headquarters setup > Parameters**.

1. On the left navigation, select **Customer orders**. On the **Payments** tab, make sure the **Terms of payment** and **Method of payment** are set up correctly.












