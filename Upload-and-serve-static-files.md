---
# required metadata

title: Upload and serve static files 
description: This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.
author: StuHarg
manager: annbe
ms.date: 10/26/2020
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

[!include [banner](includes/banner.md)]

This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.

## Overview

Some third party connectors require a file be hosted and served from the e-commerce site, which serves as a callback URL. These connectors expect the file to be returned by requests to a specific URL path and file name. This help topic explains how to upload and serve a static file on a Dynamics 365 Commerce e-commerce site, with a user-definable URL and file name. 

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps.

1. Go to the URLs section of your site in site builder and select **+ New** -> **Create new URL**
2. Choose Media library URL
3. Enter the URL path, including the file name in the URL path field
4. Click **Next**, which will open the media library
5. Select a previously uploaded file, or click **Upload** to upload a new file
6. Click **Save**.

At this point, the URL you created is in draft state, and the file it points to will not be returned by that URL until you publish it. This allows you to validate that the correct data is being returned by the URL. 

## Validate an URL prior to publishing it

To validate an URL prior to publishing it, follow these steps.

1. Go to the URLs section of your site and select the URL you wish to preview.
2. Click on the link below the Edit button. This will launch a new browser window which will return a 404
3. Add the `preview=inprogress` query string name/value pair onto the URL (e.g. https://yoursite.com/callback.html?**preview=inprogress**)

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
