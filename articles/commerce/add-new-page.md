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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add a new site page in Dynamics 365 Commerce.

## Overview

After you have created templates and fragments for your site, the next step is to start creating pages that use them.

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

1. Under **Sites**, click **Fabrikam** (or your site name).
1. Click **New Page**.
1. In the **New Page** dialog box, select a template, then click **OK**.
1. In the **Page Name** text box, enter a page name (for example, "My New Page").
1. In the **URL** text box, enter a string to complet the URL (for example, "mynewpage").
1. Click **OK**. The page editor opens. Notice that the page automatically gets proper headers and footers from the template chosen.
1. From the **Page Outline**, select **Main Slot**.
1. Click the ellipsis button (**...**), then select **Add Module**.
1. Select **Container**, then click **OK**
1. Select **Fluid Container**, click the ellipsis button (**...**), then select **Add Module**.
1. Select **Content Rich block**, then click **OK**.
1. Select **Content Rich Block**, click the ellipsis button (**...**), then select **Add Module**. 
1. Select **Content rich block item**, then click **OK**.
1. On the right-side properties pane, click **Paragraph**, then in the text box enter "My test text".
1. Click **Save**, then click **Check In**. In the **Comments** text box, enter "Added new page", then click **OK**.
1. Click **Preview** to preview your page. When done, close the preview tab to return to the authoring tool.
1. Click **Publish**.
1. From the breadcrumb, click **Fabrikam** (or your site name).
1. On the left-side navigation pane, click **URLs**.
1. Locate your URL (mynewpage) from the list and select it.
1. Click **Publish**.


