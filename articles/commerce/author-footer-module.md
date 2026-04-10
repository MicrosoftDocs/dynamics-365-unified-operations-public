---
title: Footer module
description: Learn about footer modules and how to author them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/15/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Footer module  

[!include [banner](includes/banner.md)]

This article covers footer modules and describes how to create them in Microsoft Dynamics 365 Commerce.

The footer module is a special container that hosts the modules that appear in the page footer. For example, it can include links to various pages across the site, such as **Contact Us** and **Store Policies** pages.

The following image shows an example of a footer module on a site page.

:::image type="content" source="./media/ecommerce-footer.PNG" alt-text="Screenshot of an example footer module on an e-commerce site page.":::

## Footer module properties 

Like most containers, a footer module supports properties for the heading and the width. It also supports the addition of multiple footer category modules. Each footer category module that you add renders as a column in the footer module.

## Modules available in a footer module

**Footer item** – A footer item module can contain either a heading or a link. Use the heading as a footer section title. Every link in the footer can be configured so that it has just text (for example, "Contact Us" and "Privacy" links), or so that it has both text and an image (for example, social media links). If you provide both a heading and link, the heading property takes precedence over the link. 

**Back to top** – A back to top module provides a link for quick navigation to the top of the page. A destination is required. The default destination value is \#, which takes the user to the top of the page.

## Create a footer module

To create a footer module, follow these steps:

1. Go to **Fragments**, and select **New** to create a new fragment.
1. In the **Select a fragment** dialog box, select the **Container** module, enter a name for the fragment, and then select **OK**.
1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Footer category** module, and then select **OK**.
1. In the **Footer category** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Footer item** module, and then select **OK**.
1. Select the **Footer item** slot, and then, in the properties pane on the right, configure the heading, link and link text, and image as needed.
1. To add more footer items, repeat steps 5 through 7 for each.
1. To add a "back to top" link to your footer, select the ellipsis (**...**) in the **Footer category** slot, and then select **Add module**.
1. In the **Select modules** dialog box, select the **Back to top** module, and then select **OK**.
1. Select the **Back to top** slot, and then, in the properties pane on the right, configure the text and other module properties as needed.
1. Select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

To help guarantee that a footer appears on every page, follow these steps on every page template that you create for the site.

1. In the **Footer** slot of the **Default page** module, add the footer fragment that you created.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.

By adding the fragment to page templates, you help guarantee that the footer is rendered on every page.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
