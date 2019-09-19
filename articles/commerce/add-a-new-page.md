---
# required metadata

title: Add a new site page
description: This topic describes how to add a new site page in Dynamics 365 Commerce.
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

# Add a new site page

This topic describes how to add a new site page in Dynamics 365 Commerce.

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

## Overview

After you have finished with your templates and fragments, next step is to start creating pages that utilize them.

First, you need to open the authoring tool and navigate to the site you would like to add the new page on. Make sure that "Pages" is selected from the action ribbon, no pages are selected and then proceed to activate the "New page"-button.

You will be presented with a new page dialog where you are asked which template you would like to use for the new page.  You are also required to enter the name for the new page and you can optionally enter the URL for the page.

### Template
You can choose to use either Layout or Template for your new page. For more information on Layouts, please see (link here) and for Templates, please see (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/niholman-Templates-and-layouts/articles/commerce/Templates-and-layouts.md#create-a-new-template).

### Page Name
Page Name is unique to your page. You should give your page a descriptive name so that you are able to find it easily in the future and so that other people know what the page is used for. Choose the page name carefully, it cannot be changed later.

### URL
You have the option of entering URL for your new page. If you choose to enter the URL at the time of new page creation, new URL is created and your new page is assigned to that URL. You can change the URL at later time before publishing the page. For more information about URLs, please see (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/pull/5732/files#diff-52d02a4ac5f62ea90af3f36617ffa0ce).

When you have entered all the required information and press "OK", the page is created and page editor opens to your new page with it checked out to you. The "Page Outline"-view reflects the structure of the template you selected for your new page. You may continue modifying your page or create another one.

Note: Dynamics 365 e-Commerce feature decouples URLs and content. Page can be created without associating it with an URL and vice versa. This allows switching the content for an URL with zero downtime and allows easy management of redirections.

For more information on page editing, please see the following articles
- (Chris to reconcile : https://github.com/MicrosoftDocs/Dynamics-365-Operations/pull/5781/files#diff-c38debc450971f13ad973303bba03074)

### Add a new page

To add a new site page to your site, do the following.

1. Locate and click **Fabrikam**-site under **Sites**
1. Click **New Page** from the action bar
1. In the **New Page** dialog box, select a template.
1. Add **Page Name**, e.g. "My New Page"
1. Add **URL**, e.g. "mynewpage"
1. Click **OK**. You will be sent to the page editor. Notice that the page automatically gets proper headers and footers from the template
1. From the **Page Outline**, select **Main Slot**
1. Open the ellipsis-menu right of **Main Slot**
1. Select **Add Module** from the menu
1. Select **Container** and click **OK**
1. Open the ellipsis-menu right of **Fluid Container**
1. Select **Add Module** from the menu
1. Choose **Content rich block** from the list and click **OK**
1. Open the ellipsis-menu right of **Content Rich Block**
1. Select **Add Module** from the menu
1. Choose **Content rich block item** from the list and click **OK**
1. From the module inspector on the right side of the screen, locate and click **Paragraph** property
1. Type in "My test text"
1. Click **Save** from the action bar
1. Click **Check In** from the action bar, in the **Comments**-field write "Added new page" and click **OK**
1. Click **Preview** from the action bar to preview your page
1. Close the preview-tab to get back to the authoring tool
1. Click **Publish** from the action bar
1. Click **Fabrikam** (your site name) from the breadcrumb
1. Click **URLs** from the menu on the left
1. Locate your URL (mynewpage) from the list and select it
1. Click **Publish** from the action bar


