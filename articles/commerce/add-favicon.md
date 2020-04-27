---
# required metadata

title: Add a favicon
description: This topic explains how to add a favicon to your site.
author: bicyclingfool
manager: annbe
ms.date: 04/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
ms.author: StuHarg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Add a favicon

[!include [banner](includes/banner.md)]

This topic explains how to add a favicon to your site.

## Overview

A favicon is a small graphics file that is shown on a web browser tab, in the Address bar, in the browsing history, and in bookmarks or favorites, among other places. We recommend that you add a favicon to your site, because it represents and reinforces your brand, and helps distinguish your site from other sites that your customers visit.

Although you can add multiple favicons of various sizes and file types to your site, this topic shows how to add a single favicon. However, the same process and location are used to add more favicons.

## Upload a favicon to your site's asset collection

To upload a favicon to your site's asset collection, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Media Items**.
1. In the File Explorer window, navigate to and select the favicon image file to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. If you want to publish the image(s) immediately after upload, select the **Publish media items after upload** check box.
1. Select **OK**.
1. In the property pane on the right, copy the public URL of the favicon for later use.

> [!NOTE]
> If you don't select the **Publish media items after upload** option, you must return to **Media items** page and manually publish the favicon later.

## Create the HTML for your favicon

To create the HTML for the favicon, use the following HTML snippet. For the **href** attribute, replace **Public\_URL\_for\_your\_favicon** with the public URL that you copied earlier.

`<link rel="shortcut icon" href="Public_URL_for_your_favicon">`

## Create a page fragment to contain a metatag for your favicon

To create a page fragment to contain a metatag for your favicon, follow these steps.

1. Go to **Page fragments** and select **+New**.
1. In the **New Page Fragment** dialog box, select the **Metatags** module as the module to base this page fragment on.
1. Enter a name for the page fragment, and then select **OK**.
1. In the fragment hierarchy tree, select the **Default metatags** child.
1. In the right pane under **Meta Tags**, select **+Add**, and then enter the HTML string that you created above for the favicon. 
1. Select **Finish editing**, and then select **Publish** to publish the page fragment.

## Add the metatag page fragment to the HTML head section of your pages

To add the metatag page fragment to the HTML head section of your pages, follow these steps.

1. Go to **Templates**, open the template for the pages that you wish to add your favicon to, and then select **Edit**.
1. In the template hierarchy tree, select the ellipsis (**...**) to the right of the **HTML head** container, and then select **Add page fragment**.
1. In the **Select Page Fragment** dialog box, select the metatag page fragment you created previously, and then select **OK**.
1. Select **Finish editing**, and then select **Publish** to publish the template.

> [!NOTE]
> If your site uses more than one template, you will need to add the metatags page fragment to all of them.  

When you preview pages that are based on the template to which you added the metatags page fragment, you will now see the favicon appear in the browser tab.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a welcome message](add-welcome-message.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

