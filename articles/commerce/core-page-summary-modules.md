---
# required metadata

title: Page summary modules
description: This topic covers the page summary modules and describes how to add one to a template in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 02/11/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Page summary modules

[!include [banner](includes/banner.md)]

This topic covers the page summary modules and describes how to add one to a template in Microsoft Dynamics 365 Commerce.

Page summary modules simplifies entry of page summary metadata which can be used by search engines and social sharing sites, including the canonical link.  The module library contains several page summary modules including **Page summary**, **Category page summary**, **List page summary** and **Product page summary** pages.  Each one is SEO tuned for the specific page types they will be used for. 

![Page module slots](media/page-module-1.png)

## Page module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Skip to main content text | Text | Text to be displayed in the "skip to main content" link on a page. |
| Theme             | A list of available themes will be shown | Specifies the theme to use for the pages derived from this template.  **Note: this configuration property has been deprecated and will be removed in a future release. Themes should only be set at the site level.**
| Requires sign-in? | **True** or **False** | This boolean property controls whether the page requires sign-in to be accessed.  If set to true the user will be redirected to the sign in page if not signed in. |

## Adding a page module to a template

1. From within a site builder template select the **Add Module** option within the **...** of the **HTML Head** slot and select the page summary module followed by the **OK** button as shown below.

![Add new module](media/page-summary-1.png)

Once the summary module is added it should look similar to the below iamge.  The module can now be configured and the template can be saved and published.

![Page summary module added](media/page-summary-2.png)

## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](core-default-page-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
