---
# required metadata

title: \"Pick this up\" option not displayed on cart or product details pages
description: This topic provides troubleshooting guidance for when the option to pick up in store isn't displayed on the cart or product details pages. 
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

# "Pick this up" option not displayed on cart or product details pages

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when the option to pick up in store isn't displayed on the cart or product details pages.

## Description

The **Pick this up** option isn't displayed on the cart or product details pages, as shown in the following example image.

![Pick this up option](media/pickup-button-missing.jpg)

## Resolution

### Enable "BOPIS" extension in Commerce site builder

To enable the "BOPIS" extension in Commerce site builder, follow these steps.

1. Select your site.
1. Select **Site settings**, and then select **Extensions**.
1. Confirm that the **Disable BOPIS** option is not selected.

### Configure modes of delivery in Commerce headquarters

To configure modes of delivery in Commerce headquarters, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Modes of delivery**.
1. Confirm that a **Customer pickup** mode of delivery has been created, and that products and addresses are assigned to it.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters**.
1. Select **Customer orders** on the left navigation pane.
1. Confirm that the **Pickup mode of delivery** is configured correctly.

### Configure customer orders payments

To configure customer orders payments in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters**.
1. On the left navigation, select **Customer orders**. On the **Payments** FastTab, confirm that the **Terms of payment** and **Method of payment** drop-down list options are correct.

### Additional resources

[Configure BOPIS](../cpe-bopis.md)

[Enable multiple pickup delivery modes for customer orders](../multiple-pickup-modes.md)

[Omni-channel Commerce order payments](../dev-itpro/commerce-payments.md)

[Store selector module](../store-selector.md)
