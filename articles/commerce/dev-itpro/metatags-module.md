---
title: Metatags module
description: Learn about metatags modules and how to add them to templates in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Metatags module

[!include [banner](../includes/banner.md)]

This article explains metatags modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.

The metatags module supports the entry of custom HTML meta tags that can help improve search engine optimization (SEO) rankings for site pages.

Add the metatags module to a template's **HTML Head** slot. You can configure it in the template and on the site pages that come from the template.

You can add one or more general meta tags to a template. However, add page-specific meta tags to the relevant site pages. Page-level meta tags overwrite template-level meta tags. 

The following illustration shows an example where a metatags module is added to the **HTML Head** slot of a template.

:::image type="content" source="../media/metatags-module-1.png" alt-text="Screenshot of metatags modules in the HTML Head slot of a template.":::

## Metatags module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Meta Tags | Text | Add one or more meta tags to the module. |

## Add a metatags module to a template

To add a metatags module to a template, follow these steps:

1. In Commerce site builder for your site, select **Templates**.
1. Select a template, and then select **Edit**.
1. In the **HTML Head** slot, select the ellipsis (**...**), and then select **Add module**.

    :::image type="content" source="../media/metatags-module-2.png" alt-text="Screenshot of adding a new module.":::

1. In the **Select modules** dialog box, select the **Metatags** module, and then select **OK**.

    :::image type="content" source="../media/metatags-module-3.png" alt-text="Screenshot of adding a metatags module.":::

1. To add meta tags, select the **Metatags** slot. Then, in the module properties pane, select **Add Meta Tag** to add each meta tag. You can reorder the meta tags by using the up arrow and down arrow buttons.
1. When you finish editing the template, select **Save**, select **Finish editing**, and then select **Publish** to publish it.

After you add the meta tags module to a template, you can add page-specific meta tags to the site pages that use the template.

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Default page module](default-page-module.md)

[Page summary modules](page-summary-module.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
