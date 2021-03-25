---
# required metadata

title: Metatags module
description: This topic covers metatags modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.
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

# Metatags modules

[!include [banner](includes/banner.md)]

This topic covers metatags modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.

The metatags module supports the entry of custom HTML meta tags that can improve site page search engine optimization (SEO) rankings.

The metatags module is added to a template's **HTML Head** slot, which makes the module available to configure both in the template and in the site pages derived from the template. One or more general meta tags can be added to a template, but page-specific meta tags should be added to those site pages. Page-level metatags overwrite template-level meta tags. 

The following example image shows a metatags module added to the **HTML Head** slot of a template.

![Metatags modules](media/metatags-module-1.png)

## Metatags module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Meta Tags | Text | One or more meta tags can be added to the module. |

## Add a metatags module to a template

To add a metatags module to a template, follow these steps.

1. In Commerce site builder for your site, select **Templates**. 
1. Select a template, and then select **Edit**.
1. In the **HTML Head** slot, select the ellipsis (**...**), and then select **Add Module**.

    ![Add new module](media/metatags-module-2.png)

1. In the **Add Module** dialog box, select the **Metatags*** module, and then select **OK**.

    ![Add script module](media/metatags-module-3.png)

1. To add meta tags, select the **Metatags** slot. In the module properties pane, select **Add Meta Tag** to add each meta tag. Reorder the meta tags by selecting the up or down arrows. 
1. When done editing the template, select **Save**, select **Finish editing**, and then select **Publish** to publish it.  

Once the meta tags module is added to a template, page-specific meta tags can then be added to site pages that use the template.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](default-page-module.md)

[Page summary modules](page-summary-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
