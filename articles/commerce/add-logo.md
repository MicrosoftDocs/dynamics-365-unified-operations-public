---
# required metadata

title: Add a logo to your site
description: This topic describes how to add a logo to your site in Dynamics 365 Commerce.
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

This topic describes how to add a logo to your site in Dynamics 365 Commerce.

## Overview

Probably one of the first things you'll do when building your site is to add your company or brand logo to the header of your site. The  Commerce online starter kit provides a module that makes this task easy. 

It is possible to add a logo directly into a template, layout, or page so that you can change the logo that appears on certain pages or groups of pages. However, this article will cover the most common scenario where you add your logo to a reusable header fragment that can be reused across all the pages of your site. 

## Prerequisites

Before you can add a logo to all the pages of your site, you must do the following.

1. Upload your logo to the digital assets manager, which is accessed through the Assets page. 
1. Create a header fragment. See [Work with fragments](work-with-fragments.md) for more information on creating and using fragments.
1. Include the header fragment in the template that the pages of your site use for their layout and module options. See [Work with templates](work-with-templates.md) for more information on templates. 

## Add a logo to the header fragment

To add a logo to the header fragment for your site, do the following.

1. In the left navigation pane, click **Fragments**, then click on the header fragment you created.
2. Click **Check out**.
3. Expand the **Header slot** and the **Logo slot**.
4. Click the ellipsis button (**...**) of the logo slot, then select **Add module**.
5. Select the **Logo** module. In the right-side properties pane, configure the logo module to display your logo.
7. Save, check in, and publish the header fragment.

After you publish your header fragment, all pages that use the template containing the header fragment you updated will display your logo. 

 

 

