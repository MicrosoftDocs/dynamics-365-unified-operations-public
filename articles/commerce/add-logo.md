---
# required metadata

title: Add a logo
description: This topic describes how to add a logo to your site in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry:
ms.author: stuharg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Add a logo

[!include [banner](includes/banner.md)]

This topic describes how to add a logo to your site in Microsoft Dynamics 365 Commerce.

When you build your site, one of the first things that you will probably do is add your company or brand logo to the site's header. The Dynamics 365 Commerce online module library provides a module that makes this task easy.

You can add a logo directly to a template, layout, or page. In this way, you can easily change the logo that appears on specific pages or groups of pages. However, this topic covers the most frequent scenario, where you add your logo to a header fragment that can be reused across all the pages of your site.

## Prerequisites

Before you can add a logo to all the pages of your site, you must complete these tasks.

1. Upload your logo to the Media Library.
1. Create a header fragment. For more information about how to create and use fragments, see [Work with fragments](work-with-fragments.md).
1. Include the header fragment in the template that the pages of your site use for their layout and module options. For more information about templates, see [Work with templates](work-with-templates.md).

## Add a logo to a header fragment

To add a logo to the header fragment for your site, follow these steps.

1. In the navigation pane on the left, select **Fragments**.
1. Select the header fragment that you created, and then select **Edit**.
1. Expand the header module.
1. In the property pane for the header module, provide an image and link for the logo. 
1. Save the header fragment, finish editing it, and publish it.

After you publish the updated header fragment, all site pages that use the template that contains the header fragment will show your logo.

## Additional resources

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
