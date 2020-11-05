---
# required metadata

title: Upload and serve static files 
description: This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.
author: StuHarg
manager: annbe
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8
---
# Upload and serve static files

[!include [banner](../includes/banner.md)]

This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.

## Overview

Some third-party connectors require a file to be hosted and served from the e-commerce site which then serves as a callback URL. These connectors expect the file to be returned by requests to a specific URL path and file name. This topic explains how to upload and serve a static file on a Dynamics 365 Commerce e-commerce site, with a user-definable URL and file name. 

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps.

1. Go to your site's **Media library** and upload the document that will be served by requests to the URL that you will define below. If you have already done this, you can skip this step.
1. Go to **URLs**.
1. Select **+ New \> New URL**.
1. In the **New URL** dialog box, select **Media library asset**.
1. In the **URL path** box, enter the URL path, including the file name.
1. Select **Next**, which will open the Media library and display all media assets of type "document" that have been uploaded.
1. Select the document that will be served for requests to the URL that you defined in step 5.
1. Select **Save**.

At this point, the URL you created is in draft state, and the file it points to will not be returned by that URL until you publish the URL. This allows you to validate that the correct data is being returned by the URL. 

## Validate an URL before publishing it

To validate an URL before publishing it, follow these steps.

1. Go to **URLs** for your site and select the URL you want to preview.
2. Below the **Edit** button in the properties pane on the right, select the correct URL link. This will launch a new browser window which will return a 404 error.
3. Append the `?preview=inprogress` query string to the URL (for example, `https://yoursite.com/callback.html?preview=inprogress`) and reload the page.

The file you uploaded to the Media library should be returned in the response. Once you have validated the URL, you can publish it by going to **URLs** within your site, selecting the URL, and then selecting **Publish**.

## Update the document that a URL points to

After a URL is published, you can change the file that it points to, or change the URL to a different type of resource such as an internal file or a redirect.

To update the document that a URL points to, follow these steps.

1. Go **URLs** in site builder, and then select the URL you want to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, select the **Step 2** box, and then a new document from the Media library.
1. Select **Apply**

## Update the URL to point to a different asset type

You can also update the URL to point to a different asset type such as an internal page or a redirect.

To update the URL to point to a different asset type, follow these steps.

1. Go **URLs** section in site builder, and then select the URL you want to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, select a different asset type under **Step1**.
1. Select the **Step 2** box, and then select the new asset.
1. Select **Apply**

## Change the URL path

Once a URL is created, its path cannot be modified. If you need to change the URL path that serves a file, or any other type of resource, you will need to create a new URL, map it to the existing file or other resource, and then unpublish and delete the old URL. 

To change the URL path, follow these steps.

1. Follow the steps to [Create a site URL that returns a static file](#create-a-site-URL-that-returns-a-static-file).
1. Create a new URL and enter the URL path for the URL you wish to update to.
1. Point the URL at the asset you're updating the URL for and click Save.
1. With new URL selected, select **Publish** on the command bar to publish the new URL.
1. To unpublish the old URL, select the old URL, and then select **Unpublish** on the command bar. Then delete the old URL if desired.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload videos](dam-upload-video.md)

[Upload files other than images and videos](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)
