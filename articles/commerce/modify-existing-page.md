---
# required metadata

title: Modify an existing site page
description: This topic describes how to to modify an existing site page in Dynamics 365 Commerce.
author: psimolin
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Modify an existing site page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to to modify an existing site page in Dynamics 365 Commerce.

## Overview

When you need to modify your page, you will first want to open it in the page editor.

Navigate to the site which contains your page, then from the list of pages locate the page you want to change. If you are unable to locate the page easily, you can use the rich search functionality of the authoring tool. By typing the exact page name or first few letters followed with an asterisk, you will get a filtered list of pages that helps you to locate your page. Proceed to click the page name in order to open it in the page editor.

> [!TIP]
> When you have your page visible in the page inspector, you may proceed to select it and check it out before opening it in the page editor. This allows you to check out multiple pages at the same time should you have the need to do that.

When you have the page open in the page editor, you need to make sure it is checked out to you. The action ribbon in the authoring tool is dynamic and context- and state-sensitive, which means that it only shows you the actions you can perform on the page. If the page is not checked out, you will not see "Save" or "Check in" in the action ribbon. The state of the page is also visible on the right hand side of the screen. If the page is not checked out to you, proceed to click "Check out" from the action ribbon. The action ribbon will change to reflect the new state of the page and you will also get a notification indicating that the page was checked out to you.

The next step is to implement the actual modifications. Typically you would use the "Page Outline" view to navigate to the module that you want to modify, select it, and perform modifications in the right-side properties pane. Your modification could also be adding a module, removing a module, or adding or removing a fragment. In order to add a fragment or module, use the "Page Outline" view to locate the slot you want to add your module or fragment to and then click the ellipsis button (**...**) on the right. This shows you a menu with options to add a module or fragment. If you want to remove module or fragment, you will again use the "Page Outline" view to locate the module or fragment in question and then click the ellipsis button (**...**) on the right. This will give you the option to delete the module or fragment.

>[!TIP]
> You can also click directly on a module visible in the WYSIWYG preview to show and edit its properties.

After performing your modifications and previewing them, you should check in your changes by clicking **Check in** on the action ribbon. 

If you want to publish your modifications right away, click **Publish** on the action ribbon. The latest checked-in version of the page with your modifications will then be published and available to external users viewing your site. 

### Example: Change the video on the home page

Then following is an example procedure for modifying a page.

To change the video on the home page, do the following.

1. Under **Sites**, click **Fabrikam** (or your site name).
1. On the left-side navigation pane, click **Pages**. Locate the home page and click it to open it in the page editor.
1. Click **Check Out** from the action bar.
1. From the **Page Outline**, select **Main Slot**.
1. Expand all the **Fluid container** modules under **Main Slot**.
1. Locate and select the **Video player** module.
1. In the right-side properties pane, click the **video** property. The asset picker appears.
1. From the asset picker, select an available video asset, or click **Upload new asset** to upload a new video asset.
1. Click **OK**.
1. Click **Save**, then click **Check In**. In the **Comments** text box, enter "Changed the video", then click **OK**.
1. Click **Preview** to preview your enriched product page. When done, close the preview tab to return to the authoring tool.
1. Click **Publish**.
