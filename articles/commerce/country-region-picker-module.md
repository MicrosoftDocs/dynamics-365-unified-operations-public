---
title: Country/region picker module
description: Learn about the country/region picker module and how to configure it in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-08-12
ms.custom: 
  - bap-template
---

# Country/region picker module

[!include [banner](includes/banner.md)]

This article covers the country/region picker module and describes how to configure it in Microsoft Dynamics 365 Commerce.

The country/region picker module uses the [geo detection and redirection](dev-itpro/geo-detection-redirection.md) feature in Dynamics 365 Commerce to show recommended sites to customers who request an e-commerce site URL that isn't associated with their country or region.

For example, a customer in Canada requests a site URL that is associated with a country/region other than Canada. In this case, the country/region picker module shows a dialog box that recommends site URLs that are associated with Canada.

## How it works

When you enable geo detection and redirection for a site, and a customer requests a site URL, the system uses the detected country/region for the customer and the URL that they requested to determine whether that URL is mapped to the country/region where the customer is. You define the mapping between URLs and countries/regions on the **Channels** page under **Site settings** in Commerce site builder.

If the request URL doesn't match any URL that is mapped to the customer's country or region, the list of one or more URLs that are mapped to that country or region is returned in the response. The country/region picker compares each URL in that list to the URLs that you configure in the country/region module. For every exact match that it finds, the country/region picker renders the display heading, subheading, and image for that URL, and hyperlinks those elements by using the URL.

When a customer selects an option in the country/region picker, they go to the hyperlinked URL. The URL is written to the **\_msdyn365\_\_\_site\_** cookie so that it can be used as the customer's site preference. Then, the next time that the customer requests the URL that isn't associated with their country or region, they're automatically redirected to their preferred country or region. Microsoft recommends that you also use the [site picker module](site-selector.md) on your e-commerce site, so that customers have a way to override or update their site preference.

If a customer closes the country/region picker dialog box, no cookie is written, and the customer stays on the current site.

The following illustration shows an example of the country/region picker dialog box.

:::image type="content" source="./media/Geo_country-region-module-insitu.png" alt-text="Screenshot of a country/region picker dialog box on a home page.":::

## Country/region picker module properties

| Property name              | Value       | Description                                                  |
| -------------------------- | ----------- | ------------------------------------------------------------ |
| Heading                    | Text        | The heading that appears at the top of the dialog box.       |
| Subheading                 | Text        | The subheading that appears below the heading.               |
| Country: Display string    | Text        | The display name for a URL option (for example, "Canada").   |
| Country: Display substring | Text        | An optional display substring for a URL option (for example, "English" or "French"). |
| Country: Country image     | Media asset | An optional image that is associated with a URL option (for example, an image of the Canadian flag). |
| Country: Country URL       | Text        | The site URL for the country/region that you're configuring. This URL must exactly match the URL that you specified for this country/region on the **Channels** page under **Site settings** in Commerce site builder. Additionally, the domain of the URL must be the custom domain that you specify in the **Match domain** field on the **Channels** page, not the working address of the site that Commerce provides when you create your e-commerce environment (for example, the URL `https://<yourcompany>.commerce.dynamics.com/`). |
| Action link                | Action link | An optional link that appears at the bottom of the dialog box. For example, this link can point to an internal page that provides a list of all countries and regions that the site supports. |

## Add a country/region picker module to a page

Add the country/region picker module to the header module either directly or via a shared fragment. For more information about header modules, see [Header module](author-header-module.md).

## Configure the country/region picker module in Commerce site builder

> [!NOTE]
> You must configure the URLs that you recommend to your customers as country objects in the country/region picker module.

For each site URL that you want to show and recommend to customers, follow these steps in Commerce site builder.

1. Select the country/region picker module slot.
1. In the properties pane, under **Country list**, select **Add country**.
1. Select the new **Country** box.
1. In the **Display string** field, enter a display name (for example, **Canada**).
1. Optional: In the **Display substring** field, enter a display substring (for example, **French**, or **fr-ca**).
1. Optional: Select an image from the media library.
1. In the **Country URL** field, enter the URL. This URL must exactly match the URL that appears on the **Channels** page and that is mapped to the channel, including the locale that is associated with the country or region.
1. Select **OK**.
1. Repeat these steps for any other country/region URLs that you want the country/region picker module to show.

## Additional resources

[Set up geo detection and redirection](dev-itpro/geo-detection-redirection.md)

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)

[Site picker module](site-selector.md)

[Breadcrumb module](add-breadcrumb.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
