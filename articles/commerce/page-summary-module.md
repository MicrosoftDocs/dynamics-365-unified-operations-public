---
# required metadata

title: Page summary module
description: This topic covers page summary modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 03/24/2021
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

This topic covers page summary modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.

Page summary modules simplify the entry of page summary metadata which can be used by search engines and social sharing sites, including the canonical link. The module library contains several page summary modules including **Page summary**, **Category page summary**, **List page summary** and **Product page summary** pages.  Each one is SEO tuned for the specific page types they will be used for. All summary page modules share the same set of properties defined below.

![Page module slots](media/page-module-1.png)

## Summary page module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| title | Text | The title of the web page. |
| description | Text | A brief description of the page contents. |
| keywords | Text | A series of comma separated keywords that are relevant to the page. |
| Disable Twitter Tags | **True** or **False** | If set to true twitter tags will not be rendered in the HTML. |
| Sharing Image | Image selector | Image is used for when sharing the page. |
| Disable Facebook OG Tags | **True** or **False** | If set to true Facebook tags will not be rendered in the HTML. |
| Ignores the prefix and suffix specified in the application settings | **True** or **False** | If set to true, the site level prefix and suffix setting will be ignored. |

## Adding a page module to a template

From within a site builder template select the **Add Module** option within the **...** of the **HTML Head** slot and select the page summary module followed by the **OK** button as shown below.  Ensure you add the appropriate page summary module based on the page types the template will be used for.

![Add new module](media/page-summary-1.png)

Once the summary module is added it should look similar to the below image.  The module can now be configured and the template can be saved and published.

![Page summary module added](media/page-summary-2.png)

**Note:** default values can be set in the template but can be overridden on pages that derive from the page.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](default-page-module.md)

[Script modules](script-module.md)

[Metatags module](metatags-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
