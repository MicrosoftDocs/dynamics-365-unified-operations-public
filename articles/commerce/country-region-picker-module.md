---
# required metadata

title: Country/region picker module
description: This topic covers the country/region picker module and describes how to configure it in Microsoft Dynamics 365 Commerce. 
author: stuharg
ms.date: 03/21/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata
# ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: v-chgri
# ms.tgt\_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
ms.search.industry:
ms.author: stuharg
ms.search.validFrom: 2021-08-12
ms.dyn365.ops.version: Release 10.0.22

---

# Country/region picker module

[!include [banner](includes/banner.md)]

This topic covers the country/region picker module and describes how to configure it in Microsoft Dynamics 365 Commerce.

The country/region picker module uses the [geo detection and redirection](geo-detection-redirection.md) feature in Dynamics 365 Commerce to show recommended sites to customers who request an e-commerce site URL that isn't associated with their country or region.

For example, a customer in Canada requests a site URL that is associated with a country other than Canada. In this case, the country/region picker module shows a dialog box that recommends site URLs that are associated with Canada. 

## How it works

When geo detection and redirection are enabled for a site and a customer requests a site URL, their detected country and the URL they requested are used to determine whether the requested URL is mapped to the country they're in. That mapping between URLs and countries is defined in site builder on the **Site settings \> Channels** page. 

If the request URL does not match any URL mapped to the customer's country, the list of one or more URLs that are mapped to their country is returned in the response. The country/region picker compares each URL in that list to the URLs that have been configured in the country/region module. For every exact match found, the country/region picker renders the display heading, subheading, and image for that URL, and hyperlinks those elements with the URL.

When a customer selects on an option in the country/region picker, they are taken to the hyperlinked URL and that URL is written to the **\_msdyn365\_\_\_site\_** cookie to be used as the customer's site preference. The next time they request the URL that isn't associated with their country or region, they are automatically redirected to their preferred country. For this reason, it is also recommended to use the [site picker module](site-selector.md) on your e-commerce site so that customers have a way to override or update their site preference. 

If a customer closes the country/region picker dialog box, no cookie is written and they stay on the current site. 

The following illustration shows an example of the country/region picker dialog box.

![Example of a country/region picker dialog box on a home page.](./media/Geo_country-region-module-insitu.png)

## Country/region picker module properties

| Property name              | Value       | Description                                                  |
| -------------------------- | ----------- | ------------------------------------------------------------ |
| Heading                    | Text        | The heading that appears at the top of the dialog box.       |
| Subheading                 | Text        | The subheading that appears below the heading.               |
| Country: Display string    | Text        | The display name for a URL option (for example, "Canada").   |
| Country: Display substring | Text        | An optional display substring for a URL option (for example, "English" or "French"). |
| Country: Country image     | Media asset | An optional image that is associated with a URL option (for example, an image of the Canadian flag). |
| Country: Country URL       | Text        | The site URL for the country/region being configured. This URL must exactly match the URL that you specified on the site builder **Site settings \> Channels** page for this country/region. Additionally, the domain in the URL must be the custom domain that is specified in the **Match domain** drop-down list on the **Channels** page, and not the working address for the site (for example, the `https://<yourcompany>.commerce.dynamics.com/`) URL that is provided by Commerce when you create your e-commerce environment. |
| Action link                | Action link | An optional link that appears at the bottom of the dialog box. For example, this link can point to an internal page that provides a list of all countries and regions that the site supports. |

## Add a country/region picker module to a page

The country/region picker module can be added to the header module either directly or via a shared fragment. For more information about header modules, see [Header module](author-header-module.md).

## Configure the country/region picker module in Commerce site builder

> [!NOTE]
> The URLs that you recommend to your customers must be configured as country objects in the country/region picker module.

For each site URL that you want to show and recommend to customers, follow these steps in Commerce site builder.

1. Select the country/region picker module slot.
1. In the properties pane, under **Country list**, select **Add country**.
1. Select the new **Country** box.
1. In the **Display string** field, enter a display name (for example, **Canada**).
1. Optional: In the **Display substring** field, enter a display substring (for example, **French**, or **fr-ca**).
1. Optional: Select an image from the media library.
1. In the **Country URL** field, enter the URL. This URL must exactly match the URL that appears on the **Channels** page and is mapped to the channel, including the locale that is associated with the country or region. 
1. Select **OK**.
1. Repeat these steps for any other country URLs that you want the country/region picker module to show.

## Additional resources

[Set up geo detection and redirection](geo-detection-redirection.md)

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)

[Site picker module](site-selector.md)

[Breadcrumb module](add-breadcrumb.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
