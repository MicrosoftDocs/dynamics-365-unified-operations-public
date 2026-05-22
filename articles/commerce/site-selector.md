---
title: Site picker module
description: Learn about the site picker module and how to add it to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-10
ms.custom: 
  - bap-template
---

# Site picker module

[!include [banner](includes/banner.md)]

This article describes the site picker module and how to add it to site pages in Microsoft Dynamics 365 Commerce.

When a business has different sites across markets, regions, and locales, site users need an easy way to switch between sites and select their preferred shopping site. To accommodate this scenario, the site picker module lets users browse across multiple sites. A site picker is also recommended when you implement [geo detection and redirection](dev-itpro/geo-detection-redirection.md) for your e-commerce site, so that customers have a way to override the site preference that they indicate by using the [country/region picker](country-region-picker-module.md) module. 

You must configure the site picker module with the list of sites (markets, regions, or locales) that site users can browse. The following illustration shows an example of a site picker module that is featured in the header of a site page.

:::image type="content" source="./media/ecommerce-sitepicker.PNG" alt-text="Screenshot of a site picker module in the header of a site page.":::

## Site picker module properties

| Property name | Value                 | Description |
|---------------|-----------------------|-------------|
| Heading       | Text                  | The heading for the module. |
| Site options  | Name, Image, URL      | This property specifies a name, a link to the site's home page, and an optional image to show for each site that you include in the module. The image can be a flag, or some representation of a market, region, or locale. |

## Add a site picker module to a page

Add the site picker module to the **Site picker** slot of the [header module](author-header-module.md). After you add a site picker module, you can define the module heading and site options. Generally, a header module is contained in a header fragment that can be shared across e-commerce pages for a site. 

To add the site picker module to a header module, follow these steps:

1. In the **Site picker** slot of the header fragment's header module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Select modules** dialog box, add a **Site picker** module, and then select **OK**.
1. In the **Site picker** properties pane, select **Add site options list**. An editable **Site options list** option appears.
1. Select **Site options list**. The **Site options list** dialog box appears.
1. Under **Site name**, enter the site name text that appears in the site picker drop-down list.
1. Under **Site redirect URL**, select **Add a link**. The **Add a link** flyout pane appears.
1. In the **Add a link** flyout pane, select **Custom page**, and then select **Next**.
1. From the site URL list, select the URL with the path you created when adding the channel to the site (for example, `www.adventure-works.com/fr-ca`), and then select **Apply**.
1. Select **OK**.
1. Select **Save**, and then select **Finish editing**.
1. Select **Publish** to publish the page.

In the following example, the site picker module is added to the **Site picker** slot of a header module. The header module is contained in a header fragment that is named **HeaderContainer**.

:::image type="content" source="./media/ecommerce-sitepicker-2.png" alt-text="Screenshot of a site picker module in a header fragment.":::

## Additional resources

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)

[Breadcrumb module](add-breadcrumb.md)

[Navigation menu module](nav-menu-module.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
