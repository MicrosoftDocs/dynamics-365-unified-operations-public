---
# required metadata

title: Products and categories don't appear in Commerce site builder after a new site is mapped
description: This topic provides troubleshooting guidance for when products and categories aren't displayed in Dynamics 365 Commerce site builder after a new site is mapped. 
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

# Products and categories don't appear in site builder

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when products and categories aren't displayed in Dynamics 365 Commerce site builder after a new site is mapped.

## Description

Products and categories aren't displayed in Commerce site builder after a new site is mapped. 

## Resolution

### Add products to channel categories in Commerce headquarters

To add products to channel categories in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. In the left navigation pane, select the category that should be displayed on the e-commerce site.
1. On the **Products** FastTab, select **Add**.
1. In the **Available Products** section, select the products that you want to be displayed, and then select **Add**. 
1. Select **OK**.
1. Once the products appear on the **Products** FastTab, select **Publish channel updates** on the Action Pane.

## Additional Resources

[Configure a channel to use a channel navigation hierarchy](../configure-channel-hierarchy.md)
