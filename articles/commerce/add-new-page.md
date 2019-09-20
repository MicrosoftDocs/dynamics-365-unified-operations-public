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

After you have created templates and fragments for your site, the next step is to start creating pages that use them. To get started, you will need to select a template or layout, a page name, and a page URL.

### Template or layout
You can choose to use either a template or a layout for your new page. For more information, see [Templates and layouts overview](templates-layouts-overview.md)

### Page name
The page name must be unique to your page. It should be descriptive so that you are able to find it easily and other people know what the page is used for. Choose the page name carefully, since it cannot be changed later.

### URL
You have the option of entering a URL for your new page. If you choose to enter the URL at the time of new page creation, a new URL is created and your new page is assigned to that URL. You can change the URL at later time before publishing the page. For more information, see [Create a page URL](create-page-URL.md).

> [!NOTE]
> Commerce decouples URLs and content, meaning that a page can be created without associating it with an URL, or vice versa. This enables content swapping for an URL without downtime and easy management of redirections.

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


