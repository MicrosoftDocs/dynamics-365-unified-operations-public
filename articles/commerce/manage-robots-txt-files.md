---
title: Manage robots.txt files
description: This article describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-12-18
ms.custom: 
  - bap-template
---

# Manage robots.txt files

[!include [banner](includes/banner.md)]

This article describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.

The robots exclusion standard, or robots.txt, is a standard that websites use to communicate with web robots. It instructs web robots about any areas of a website that should not be visited. Robots are often used by search engines to index websites.

To exclude robots from a server, you create a file on the server. In this file, you specify an access policy for robots. The file must be accessible via HTTP at the local URL **/robots.txt**. The robots.txt file helps search engines index the content on your site.

Dynamics 365 Commerce lets you upload a robots.txt file for your domain. For each domain in your Commerce environment, you can upload one robots.txt file and associate it with that domain.

For more information about the robots.txt file, visit [The Web Robots Pages](https://www.robotstxt.org/).

## Upload a robots.txt file

After you've created and edited your robots.txt file according to the [robots exclusion standard](https://www.robotstxt.org/orig.html), make sure that the file is accessible on the computer where you will use the Commerce authoring tools. The file must be named **robots.txt**. For best results, it must be in the format that is noted in the standard. Each Commerce customer is responsible for validating and maintaining the contents of its robots.txt file. To upload a robots.txt file, you must be signed in to Commerce as a system admin.

To upload a robots.txt file in Commerce, follow these steps.

1. Sign in to Commerce as a system admin.
2. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
3. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
4. Select **Manage** to upload a robots.txt file for a domain in your environment.
5. On the menu on the right, select the **Upload** button (the upward-pointing arrow) next to the domain that is associated with the robots.txt file. A file browser dialog box appears.
6. In the dialog box, browse to and select the robots.txt file that you want to upload for the associated domain, and then select **Open** to complete the upload.

> [!NOTE] 
> During upload, Commerce verifies that the file is a text file, but it doesn't validate the file's contents.

## Download a robots.txt file

To download a robots.txt file in Commerce, follow these steps.

1. Sign in to Commerce as a system admin.
2. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
3. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
4. Select **Manage** to download a robots.txt file for a domain in your environment.
5. On the menu on the right, select the **Download** button (the downward-pointing arrow) next to the domain that is associated with the robots.txt file. A file browser dialog box appears.
6. In the dialog box, go to the desired location on your local drive, confirm or enter a file name, and then select **Save** to complete the download.

> [!NOTE]
> This procedure can be used to download only robots.txt files that were previously uploaded via the Commerce authoring tools.

## Delete a robots.txt file

To delete a robots.txt file in Commerce, follow these steps.

1. Sign in to Commerce as a system admin.
2. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
3. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
4. Select **Manage** to delete a robots.txt file for a domain in your environment.
5. On the menu on the right, select the **Delete** button (the trash can symbol) next to the domain that is associated with the robots.txt file. A file browser window appears.
6. In the file browser window, browse to and select the robots.txt file that you want to delete for the domain, and then select **Open**. A warning message box appears.
7. In the message box, select **Delete** to confirm deletion of the robots.txt file.

> [!NOTE] 
> This procedure can be used to delete only robots.txt files that were previously uploaded via the Commerce authoring tools.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Upload URL redirects in bulk](dev-itpro/upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](dev-itpro/set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
