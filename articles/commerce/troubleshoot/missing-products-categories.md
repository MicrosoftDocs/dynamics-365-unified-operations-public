---
# required metadata

title: Products and categories missing after environment copy
description: This topic helps troubleshoot when after a site is copied from one environment to another or within an environment, the products and categories are missing form the site. 
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

# Products and categories missing after environment copy

[!include [banner](../../includes/banner.md)]

## Description
After a site is copied from one environment to another or within an environment the products and categories are missing form the site. The products and categories will be missing from the e-Commerce storefront
and from the **Products** tab in site builder.

## Resolution

### Map the OUN to the newly copied site
1. Open site builder.

1. Select the site you are working on from on the **Sites** page.

1. Select **Channels** on the left-hand navigation bar.

1. Select the ellipses (**...**) near **Channel** and select **Map different OUN**.

1. Select the channel you want to map to the site and select **OK**.

1. Select **Save and publish** on the top navigation bar.

## Additional Resources
- [Associate a Dynamics 365 Commerce site with an online channel)(../associate-site-online-store.md)


