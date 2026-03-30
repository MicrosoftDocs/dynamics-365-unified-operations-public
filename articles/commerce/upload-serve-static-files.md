---
title: Upload and serve static files
description: Learn how to upload and serve static files in Microsoft Dynamics 365 Commerce site builder.
author: bicyclingfool
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Upload and serve static files

[!include [banner](includes/banner.md)]

This article describes how to upload and serve static files in Microsoft Dynamics 365 Commerce site builder.

Some partner connectors require that you host and serve a file from the e-commerce site. These connectors expect that requests to a specific callback URL path and file name return the file. Therefore, this article explains how to upload and serve a static file that has a user-definable URL and file name on a Dynamics 365 Commerce e-commerce site.

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps:

1. Go to your site's Media library, and upload the file that requests to the URL you define should serve. If you already uploaded the file, you can skip this step.
1. Go to **URLs** for your site.
1. Select **New \> New URL**.
1. In the **New URL** dialog box, select **Media library asset**.
1. In the **URL path** field, enter the URL path. Include the file name in the path.
1. Select **Next**. The Media library opens and shows all media assets of the **document** type that you uploaded.
1. Select the file that requests to the URL you defined in step 5 should serve.
1. Select **Save**.

At this point, the URL that you created is in a draft state. The URL doesn't return the file until you publish the URL. Before you publish the URL, you can validate that it returns the correct data.

## Validate and publish a URL

To validate a URL before you publish it, follow these steps:

1. Go to **URLs** for your site, and select the URL to preview.
1. In the properties pane on the right, below the **Edit** button, select the correct URL link. A new browser window opens, and you should receive a 404 error.
1. Append the **?preview=inprogress** query string to the URL (for example, `https://yoursite.com/callback.html?preview=inprogress`), and reload the page. The file that you uploaded to the Media library should be returned in the response.

After you validate the URL, you can publish it.

1. Go to **URLs** for your site, and select the URL.
1. Select **Publish** on the command bar.

## Update the file that a URL points to

After you publish a URL, you can update it so that it points to a different file. Alternatively, you can update the URL so that it points to a different type of resource, as described in the next section. For example, you can point the URL to an internal page or a redirect.

To update the file that a URL points to, follow these steps:

1. Go to **URLs** for your site, and select the URL to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, select the **Step 2** box, and then select a new document from the Media library.
1. Select **Apply**.

## Update the asset type that a URL points to

You can also update a URL so that it points to a different type of asset (resource), such as an internal page or a redirect.

To update the asset type that a URL points to, follow these steps:

1. Go to **URLs** for your site, and select the URL to update.
1. In the properties pane on the right, select **Edit**.
1. Under **URL assignment**, under **Step 1**, select a different asset type.
1. Select the **Step 2** box, and then select the new asset.
1. Select **Apply**.

## Change the URL path

After you create a URL, you can't change its path. If you must change the URL path that serves a file or any other type of resource, you need to create a new URL, map it to the existing file or other resource, and then unpublish and delete the old URL.

To change the URL path, follow these steps:

1. To create a new URL and map it to the existing file or another resource, follow the instructions in the [Create a site URL that returns a static file](#create-a-site-url-that-returns-a-static-file) section earlier in this article.
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
