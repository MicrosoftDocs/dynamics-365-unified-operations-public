---
# required metadata

title: Default page module
description: This topic describes the default page module and how to add it to a page template in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 03/25/2021
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

# Default page module

[!include [banner](includes/banner.md)]

This topic describes the default page module and how to add it to a page template in Microsoft Dynamics 365 Commerce.

The default page module is a special module that becomes the root of a page and can only be added to a template's **Body** slot. Only one default page module is available with the Commerce module library, but additional default page modules can be created using the [online channel extensibility SDK](e-commerce-extensibility/overview.md) as needed. The default page module defines the core slots ("Header Slot," "Sub Header Slot," "Main Slot," "Sub Footer Slot," and "Footer Slot") that will appear in the Commerce site builder page editor, as shown in the following image.

![Page module slots](media/page-module-1.png)

## Page module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Skip to main content text | Text | Text to be displayed in the "skip to main content" link on a page. |
| Theme             | A theme picked from a list of available themes. | Specifies the theme to use for the pages derived from this template.  **Note: this configuration property has been deprecated and will be removed in a future release. Themes should only be set at the site level.**
| Requires sign-in? | **True** or **False** | This boolean property controls whether the page requires user sign-in to be accessed. If set to **True**, users who are not signed-in will be redirected to the sign-in page. |

## Add a default page module to a template

To add a default page module to a template, follow these steps.

1. In site builder for your site, select **Templates**. 
1. Select a template, and then select **Edit**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add Module**.

    ![Add new module](media/page-module-2.png)

1. In the **Add Module** dialog box, select the **Default Page** module, and then select **OK**.

    ![Add default page module](media/page-module-3.png)

Once the default page module is added, it should look similar to the following example image. The module can now be configured and the template can be saved and published.

![Default page module added](media/page-module-4.png)

## Additional resources

[Module library overview](starter-kit-overview.md)

[Page summary modules](page-summary-module.md)

[Script modules](script-module.md)

[Metatags module](metatags-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
