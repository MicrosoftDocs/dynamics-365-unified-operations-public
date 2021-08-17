---
# required metadata

title: Country/region picker module
description: This topic describes how to add the country/region picker module to a site page in Microsoft Dynamics 365 Commerce, and how to configure it to display site options for your customers. 
author: stuharg
ms.date: 09/03/2021
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

# Country and region picker module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the country/region picker module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

The country/region picker is used with the [geo detection and redirection](geo-redirection.md) feature to display recommended URLs to customers who request a URL that is not associated with their country/region. 

The following illustration shows a country/region picker displayed on the home page of a site. In this example, a customer who lives in Canada requests a site URL that is not associated with Canada. The country/region picker displays and recommends sites that are associated with Canada. 

![Example of a country/region picker module displaying on a home page.](./media/Geo_country-region-module-insitu.PNG)

## Add a country/region picker module to a page

The country/region picker module can be added to the [Header module](author-header-module.md). After it's added, you can configure the module heading and properties.

## Country/region picker module configuration 

The URLs that you'll recommend to your customers must be configured as Country objects in the module. Follow these steps for each URL that you want to recommend to customers:

1. Select **+ Add country** under **Country list**. 
1. Click on the newly-created box that says "Country".
1. Enter a display string (for example, "Canada").
1. Enter an optional display substring (for example, "French", or "fr-ca"). 
1. Enter an optional image from the media library.
1. Enter the Country URL. This URL must exactly match the URL in the Channels page that is mapped to the channel and locale associated with this country. 
1. Select **OK** and repeat as necessary for the countries you wish to display in the country/region picker. 

## Country/region picker module properties

| Property name              | Value       | Description                                                  |
| -------------------------- | ----------- | ------------------------------------------------------------ |
| Heading                    | Text        | The heading that displays at the top of the module.          |
| Sub heading                | Text        | Smaller text that displays below the heading.                |
| Country: display string    | Text        | Display name for a URL option in the country/region picker ("Canada" in the example screenshot above). |
| Country: display substring | Text        | Optional display substring for a URL option ("English" and "French" in the example screenshot above). |
| Country: Country image     | Media asset | Optional image associated with the URL option (Canadian flag image in the example screenshot above). |
| Country: Country URL       | Text        | The URL that corresponds to the channel and locale for this country in the Channels page. This URL must exactly match the URL as configured in the Channels page. |
| Action link                | Action link | Optional link that displays at the bottom of the country/region picker. This link can link to an internal page and be used to offer a list of all countries supported by this site. |

## Additional resources

[Geo detection and redirection feature](geo-redirection.md)

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)




[!INCLUDE[footer-include](../includes/footer-banner.md)]
