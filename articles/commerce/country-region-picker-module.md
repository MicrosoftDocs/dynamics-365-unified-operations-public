---
# required metadata

title: Country/region picker module
description: This topic covers the country/region picker module and describes how to configure it in Microsoft Dynamics 365 Commerce. 
author: stuharg
ms.date: 09/01/2021
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
ms.author: anupamar
ms.search.validFrom: 2021-08-12
ms.dyn365.ops.version: Release 10.0.22

---

# Country/region picker module

[!include [banner](includes/banner.md)]

This topic covers the country/region picker module and describes how to configure it in Microsoft Dynamics 365 Commerce.

The country/region picker module uses the [geo detection and redirection](geo-detection-redirection.md) feature in Dynamics 365 Commerce to show recommended URLs to customers who request an e-commerce site URL that isn't associated with their country or region.

For example, a customer in Canada requests a site URL that isn't associated with Canada. In this case, the country/region picker module shows a dialog box that recommends site URLs that are associated with Canada. The following illustration shows an example of the country/region picker dialog box.

![Example of a country/region picker dialog box on a home page.](./media/Geo_country-region-module-insitu.png)

## Country/region picker module properties

| Property name              | Value       | Description |
| -------------------------- | ----------- | ----------- |
| Heading                    | Text        | The heading that appears at the top of the dialog box. |
| Subheading                 | Text        | The subheading that appears below the heading. |
| Country: Display string    | Text        | The display name for a URL option (for example, "Canada"). |
| Country: Display substring | Text        | An optional display substring for a URL option (for example, "English" or "French"). |
| Country: Country image     | Media asset | An optional image that is associated with a URL option (for example, an image of the Canadian flag). |
| Country: Country URL       | Text        | The URL that corresponds to the channel and locale that are configured for the country or region on the **Channels** page in Commerce site builder (**Site settings \> Channels**). This URL must exactly match the URL that is configured on the **Channels** page. |
| Action link                | Action link | An optional link that appears at the bottom of the dialog box. For example, this link can point to an internal page that provides a list of all countries and regions that the site supports. |

## Add a country/region picker module to a page

The country/region picker module can be added to the header module either directly or via a shared fragment. For more information about header modules, see [Header module](author-header-module.md).

## Configure the country/region picker module in Commerce site builder

> [!NOTE]
> The URLs that you recommend to your customers must be configured as country objects in the country/region picker module.

For each URL that you want to show and recommend to customers, follow these steps in Commerce site builder.

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
