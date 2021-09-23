---
# required metadata

title: Upload and serve static files
description: This topic describes how to upload a static file into Microsoft Dynamics 365 Commerce site builder, and how to create a custom URL and file name that can be used to request that file.
author: StuHarg
ms.date: 11/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic describes how to upload a static file into Microsoft Dynamics 365 Commerce site builder, and how to create a custom URL and file name that can be used to request that file.

Some third-party connectors require that a file be hosted and served from the e-commerce site. These connectors expect that the file will be returned by requests to a specific callback URL path and file name. Therefore, this topic explains how to upload and serve a static file that has a user-definable URL and file name on a Dynamics 365 Commerce e-commerce site.

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps.

1. Go to your site's Media library, and upload the file that should be served by requests to the URL that you will define. If you've already uploaded the file, you can skip this step.
1. Go to **URLs** for your site.
1. Select **New \> New URL**.
1. In the **New URL** dialog box, select **Media library asset**.
1. In the **URL path** field, enter the URL path. Include the file name in the path.
1. Select **Next**. The Media library is opened and shows all media assets of the **document** type that have been uploaded.
1. Select the file that should be served for requests to the URL that you defined in step 5.
1. Select **Save**.

At this point, the URL that you created is in a draft state. The file that the URL points to won't be returned until you publish the URL. Before you publish the URL, you can validate that it returns the correct data.

## Validate and publish a URL

To validate an URL before you publish it, follow these steps.

1. Go to **URLs** for your site, and select the URL to preview.
2. In the properties pane on the right, below the **Edit** button, select the correct URL link. A new browser window is opened, and you should receive a 404 error.
3. Append the **?preview=inprogress** query string to the URL (for example, `https://yoursite.com/callback.html?preview=inprogress`), and reload the page. The file that you uploaded to the Media library should be returned in the response.

After you've validated the URL, you can publish it.

1. Go to **URLs** for your site, and select the URL.
2. Select **Publish** on the command bar.

## Update the file that a URL points to

After a URL is published, you can update it so that it points to a different file. Alternatively, you can update the URL so that it points to a different the type of resource, as described in the next section. For example, you can point the URL to an internal page or a redirect.

To update the file that a URL points to, follow these steps.

1. Go to **URLs** for your site, and select the URL to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, select the **Step 2** box, and then select a new document from the Media library.
1. Select **Apply**.

## Update the asset type that a URL points to

You can also update a URL so that it points to a different type of asset (resource), such as an internal page or a redirect.

To update the asset type that a URL points to, follow these steps.

1. Go to **URLs** for your site, and select the URL to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, under **Step 1**, select a different asset type.
1. Select the **Step 2** box, and then select the new asset.
1. Select **Apply**.

## Change the URL path

After a URL is created, its path can't be changed. If you must change the URL path that serves a file or any other type of resource, you have to create a new URL, map it to the existing file or other resource, and then unpublish and delete the old URL.

To change the URL path, follow these steps.

1. To create a new URL and map it to the existing file or another resource, follow the instructions in the [Create a site URL that returns a static file](#create-a-site-url-that-returns-a-static-file) section earlier in this topic.
1. Select the new URL, and select **Publish** on the command bar. The new URL is published.
1. To unpublish the old URL, select it, and then select **Unpublish** on the command bar. You can now delete the old URL if you want.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload videos](dam-upload-video.md)

[Upload files other than images and videos](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]