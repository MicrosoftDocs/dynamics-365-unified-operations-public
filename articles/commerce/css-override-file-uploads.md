---
# required metadata

title: Work with CSS override files
description: This topic describes why, when, and how to use CSS override files in Microsoft Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 12/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: niholman
ms.search.validFrom: 2019-12-09
ms.dyn365.ops.version: Release 10.0.5

---
# CSS override file uploads

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes why, when, and how to use CSS override files in Microsoft Dynamics 365 Commerce.

## Overview

Under normal circumstances, permanent site styles should be handled directly through a site's theme. Themes provide the foundational CSS and style settings for modules within any given page on your site. Themes are created using the Dynamics 365 Commerce online software development kit (SDK) and deployed to your websites through Microsoft Lifecycle Services (LCS). Theme debugging capabilities and module interface configurations within the SDK help site developers create customizable and cohesive site design packages. When these design packages are deployed to a site, they enable site authors to focus on content creation, editing, and publishing rather than site development.  

With the normal lifecycle of a theme in mind, there are specific scenarios when the dependency on developers to make quick style changes through the SDK and LCS deployment pipeline can be prohibitive. Site prototypes or hotfixes can feel cumbersome if you don't have the SDK configured, or don't have time to wait for an LCS deployment. 

This is where cascading style sheet (CSS) file override uploads can help. Within the Commerce authoring tools, authenticated users can directly upload a CSS file, preview it, and then activate it to override a site's theme without the overhead of SDK or LCS deployment. The CSS override file can be as small as a single text style change, or as wide-ranging as a complete brand overhaul.  

There are two caveats to using CSS overrides: 

- Only one override file can be active on a site at any one time, therefore all active overrides must be present within a single file.

- Although you can preview override changes in the Commerce authoring tools, there are no dedicated debugging features to identify bugs introduced by the override. In other words, when using CEE overrides you do not have the same toolset provided by SDK to perform module and authoring validation.

With these caveats in mind, CSS file overrides can be a quick way to prototype a design or implement a hotfix before a full theme update is developed and deployed. 

## Create a CSS override file

To create a CSS override file, you can use any integrated development environment (IDE), text editor, or source code editor. A common approach is to use standard web debuggers in your browser to identify style selectors, properties, and values within your existing site.  Most browsers will let you change values and preview them within the debugger. Once you have identified the changes you want to make, you can save these overrides to your own CSS file.   

## Upload a CSS override file

To upload a CSS file to your site in Commerce, follow these steps.

1. Navigate to your site in the authoring tools.
1. In the navigation pane on the left, select **Design**.

    >[!NOTE]
    >Depending on your version of the Commerce authoring tools, you may first need to expand **Settings** in the navigation pane to unhide **Design**.
    
1. If it is not already selected, select the **CSS override** tab at the top of the main design pane.
1. Under the **Available CSS overrides**, click **Upload CSS file**. A File Explorer dialog box appears.
1. In File Explorer, browse to and select a CSS file and then click **Open**. Your uploaded CSS file will now appear under **Available CSS overrides**.

## Preview a CSS override file

To preview a CSS override file before making it active on your live site, follow these steps.

1. Under **Design > CSS override > Available CSS overrides**, find the CSS file you would like to preview.
1. Next to the CSS file name, click **Preview site**.
1. In the **Select a URL** dialog box, select the site URL that you want to preview with the override applied, and then click **OK**. If there are multiple variants for the selected URL, select the desired variant in the subsequent **Preview variations** dialog box.

A new browser tab or window will then open where you can validate your style overrides against your site. This URL can be shared with other authenticated Commerce users for review and feedback.

## Activate a CSS override file on your live site

After you have previewed and approved the CSS override file, you can activate on your live site.  

>[!NOTE]
>Only one CSS override file can be active on your site at a time. Activating a new override will deactivate the previous one, so ensure that all necessary overrides are present in a single CSS override file.

To activate a CSS override file, follow these steps.

1. Under **Design > CSS override > Available CSS overrides**, find the CSS file you would like to activate.
1. Under the CSS file name, click **Activate**. This will immediately make the override active on your live site.

## Deactivate a CSS override on your live site

To deactivate a CSS override from your site, follow these steps:

1. Under **Design > CSS override > Available CSS overrides**, find the CSS file you would like to deactivate.
1. Under the CSS file name, click **Deactivate**. This will immediately deactivate the CSS override on your live site.

>[!TIP]
>To display additional CSS override file options, click the ellipsis (**...**) next to the CSS override file name. The **Download**, **Rename**, and **Replace** options are useful for quick modifications to an existing override file.
