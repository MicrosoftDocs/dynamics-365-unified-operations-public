---
# required metadata

title: Upload and serve static files 
description: This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.
author: StuHarg
manager: annbe
ms.date: 10/27/2020
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

Some third party connectors require a file be hosted and served from the e-commerce site, which serves as a callback URL. These connectors expect the file to be returned by requests to a specific URL path and file name. This help topic explains how to upload and serve a static file on a Dynamics 365 Commerce e-commerce site, with a user-definable URL and file name. 

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps.

1. Go to **URLs** for your site.
1. Select **+ New \> New URL**.
2. In the **New URL** dialog box, select a Media Library URL.
3. In the **URL path** box, enter the URL path, including the file name.
4. Select **Next**, which will open the Media Library.
5. Select a previously uploaded file, or select **Upload** to upload a new file.
6. Select **Save**.

At this point, the URL you created is in draft state, and the file it points to will not be returned by that URL until you publish it. This allows you to validate that the correct data is being returned by the URL. 

## Validate an URL before publishing it

To validate an URL before publishing it, follow these steps.

1. Go to **URLs** for your site and select the URL you want to preview.
2. Below the **Edit** button in the properties pane on the right, select the correct URL link. This will launch a new browser window which will return a 404 error.
3. Add the `preview=inprogress` query string to the URL (for example, `https://yoursite.com/callback.html?preview=inprogress`).

The file you uploaded to the media library should be returned in the response. Once you have validated the URL, you can make it go live by going into the URLs section within your site, selecting the URL and clicking **Publish**.

## Update the file a URL points to

After a URL is published, you can change the file that it points to, or change the URL to a different type of resource such as an internal file or a redirect. 

## Update a URL

If you need to change the URL path that serves a file, or any other type of resource, you will need to create a new URL, map it to the existing file or other resource, and then unpublish and delete the old URL. 

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload videos](dam-upload-video.md)

[Upload files other than images and videos](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)
