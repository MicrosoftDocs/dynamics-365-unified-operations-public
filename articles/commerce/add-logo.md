---
# required metadata

title: Add a logo to your site
description: This topic describes how to add a logo to your site in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Enduser
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry:
ms.author: stuharg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Add a logo to your site

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add a logo to your site in Microsoft Dynamics 365 Commerce.

## Overview

When you build your site, one of the first things that you will probably do is add your company or brand logo to the site's header. The Dynamics 365 Commerce online starter kit provides a module that makes this task easy.

You can add a logo directly to a template, layout, or page. In this way, you can easily change the logo that appears on specific pages or groups of pages. However, this topic covers the most frequent scenario, where you add your logo to a header fragment that can be reused across all the pages of your site.

## Prerequisites

Before you can add a logo to all the pages of your site, you must complete these tasks.

1. Upload your logo to the digital assets manager, which you can access from the **Assets** page.
1. Create a header fragment. For more information about how to create and use fragments, see [Work with fragments](work-with-fragments.md).
1. Include the header fragment in the template that the pages of your site use for their layout and module options. For more information about templates, see [Work with templates](work-with-templates.md).

## Add a logo to a header fragment

To add a logo to the header fragment for your site, follow these steps.

1. In the navigation pane on the left, select **Fragments**, and then select the header fragment that you created.
2. Select **Check out**.
3. Expand the **Header** slot and the **Logo** slot.
4. Select the ellipsis button (**...**) for the **Logo** slot, and then select **Add module**.
5. Select the logo module.
6. In the properties pane on the right, configure the logo module so that it shows your logo.
7. Save the header fragment, check it in, and publish it.

After you publish the updated header fragment, all site pages that use the template that contains the header fragment will show your logo.
