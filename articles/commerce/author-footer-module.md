---
# required metadata

title: Footer module 
description: This topic covers footer modules and how to author them in Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 04/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Footer module  


[!include [banner](includes/banner.md)]

This topic covers footer modules and describes how to create them in Microsoft Dynamics 365 Commerce.

## Overview

The footer module is a special container that is used to host the modules that appear in the page footer. For example, it can include links to various pages across the site, such as **Contact Us** and **Store Policies** pages.

## Footer module properties 

Like most containers, a footer module support properties for the heading and the width. It also supports the addition of multiple footer category modules. Each footer category module that is added is rendered as a column in the footer module.

## Modules available in a footer module

**Footer items** – A footer items module can contain a heading, an image, and a link. The heading can be used either alone or in combination with an image and a link. Every link in the footer can be configured so that it has just text (for example, "Contact Us" and "Privacy" links), or so that it has both text and an image (for example, social media links).

**Back to top** – A back to top module provides a link for quick navigation to the top of the page. A destination is required. The default destination value is #, which takes the user to the top of the page.

## Author a footer module

1. In the navigation pane, select **Fragments**, and then select **New Page Fragment**.
1. In the **New Page Fragment** dialog box, select the footer module, enter a name for the page fragment, and then select **OK**.
1. In the outline tree on the left, select the ellipsis button (**...**) for the footer module, and then select **Add Module**.
1. In the **Add Module** dialog box, select the footer category module, and then select **OK**.
1. In the outline tree, select the ellipsis button for the footer category module, and then select **Add Module**.
1. In the **Add Module** dialog box, select the footer item module, and then select **OK**.
1. In the outline tree, select the footer item module. Then, in the properties pane on the right, configure the heading, link and link text, and image as you require.
1. To add more footer items, repeat steps 5 through 7.
1. To add a "back to top" link to your footer, select the ellipsis button for the footer category module, and then select **Add Module**.
1. In the **Add Module** dialog box, select the back to top module, and then select **OK**.
1. In the outline tree, select the back to top module. Then, in the properties pane on the right, configure the back to top module as you require.
1. Save the page fragment, check it in, and publish it.

On every page template that has been created for the site, follow these steps.

1. In the **Main** slot of the default page, in the footer module, add the footer fragment that you created.
1. Save the template, check it in, and publish it.

By adding the page fragment to page templates, you help guarantee that the footer is rendered on every page.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
