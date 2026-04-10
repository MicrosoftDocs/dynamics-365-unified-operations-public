---
title: Manage robots.txt files
description: Learn how to manage robots.txt files in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/03/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-12-18
ms.custom: 
  - bap-template
---

# Manage robots.txt files

[!include [banner](includes/banner.md)]

This article describes how to manage robots.txt files in Microsoft Dynamics 365 Commerce.

> [!NOTE]
> Starting February 2, 2026, a change is gradually scaling up to all customer environments where internal Commerce-generated domains (`.dynamics365commerce.ms`) return a deny-all response for robots.txt requests instead of the configured robots.txt file. This behavior prevents search engines from indexing test and staging environments. Custom production domains continue to serve the uploaded robots.txt file. To test your robots.txt configuration from an internal domain, use the `?domain=` query parameter as described in [Test robots.txt for a specific domain](#test-robotstxt-for-a-specific-domain).

The robots exclusion standard, or robots.txt, is a standard that websites use to communicate with web robots. It instructs web robots about any areas of a website that shouldn't be visited. Robots are often used by search engines to index websites.

To exclude robots from a server, create a file on the server. In this file, specify an access policy for robots. The file must be accessible via HTTP at the local URL **/robots.txt**. The robots.txt file helps search engines index the content on your site.

Dynamics 365 Commerce lets you upload a robots.txt file for your domain. For each domain in your Commerce environment, you can upload one robots.txt file and associate it with that domain.

For more information about the robots.txt file, visit [The Web Robots Pages](https://www.robotstxt.org/).

## How robots.txt works with different domain types

Robots.txt behavior differs according to which type of domain is used to access your Commerce site.

### Custom production domains

When you upload a robots.txt file for a custom domain such as `www.fabrikam.com`, that file is served when search engines or users access `/robots.txt` on your production site. This method allows search engines to index your site according to your configured rules.

### Internal Commerce-generated domains

Internal domains that use the `.dynamics365commerce.ms` format don't return uploaded robots.txt files. Instead, these domains return a deny-all response that blocks all search engine indexing. This behavior ensures that test and staging environments aren't indexed by search engines, and that only your production custom domain is crawled and indexed.

## Test robots.txt for a specific domain

To preview how your robots.txt file appears for a specific custom domain when accessing from an internal Commerce-generated domain, append the `?domain=` query parameter to the robots.txt URL.

For example, if your internal domain is `https://<e-commerce-tenant-name>.dynamics365commerce.ms` and your custom domain is `<your-custom-domain>`, use the following URL:

`https://<e-commerce-tenant-name>.dynamics365commerce.ms/robots.txt?domain=<your-custom-domain>`

This method allows you to verify the robots.txt configuration for any of your supported host names before you go live with your production domain. For more information about Commerce-generated URLs, see [Commerce-generated URLs](dev-itpro/domains-commerce.md#commerce-generated-urls). For more information about configuring custom domains, see [Configure your domain name](configure-your-domain-name.md).

## Upload a robots.txt file

After you create and edit your robots.txt file according to the [robots exclusion standard](https://www.robotstxt.org/orig.html), make sure that the file is accessible on the computer where you use the Commerce authoring tools. The file must be named **robots.txt**. For best results, use the format noted in the standard. Each Commerce customer is responsible for validating and maintaining the contents of its robots.txt file. To upload a robots.txt file, sign in to Commerce as a system admin.

To upload a robots.txt file in Commerce, follow these steps:

1. Sign in to Commerce as a system admin.
1. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
1. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
1. Select **Manage** to upload a robots.txt file for a domain in your environment.
1. On the menu on the right, select the **Upload** button (the upward-pointing arrow) next to the domain that is associated with the robots.txt file. A file browser dialog box appears.
1. In the dialog box, browse to and select the robots.txt file that you want to upload for the associated domain, and then select **Open** to complete the upload.

> [!NOTE]
> - During upload, Commerce verifies that the file is a text file, but it doesn't validate the file's contents.
> - Uploaded robots.txt files are served only on custom production domains. Internal Commerce-generated domains (such as `.dynamics365commerce.ms`) return a deny-all robots.txt response to prevent test environments from being indexed. For more information, see [How robots.txt works with different domain types](#how-robotstxt-works-with-different-domain-types).

## Download a robots.txt file

To download a robots.txt file in Commerce, follow these steps:

1. Sign in to Commerce as a system admin.
1. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
1. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
1. Select **Manage** to download a robots.txt file for a domain in your environment.
1. On the menu on the right, select the **Download** button (the downward-pointing arrow) next to the domain that is associated with the robots.txt file. A file browser dialog box appears.
1. In the dialog box, go to the desired location on your local drive, confirm or enter a file name, and then select **Save** to complete the download.

> [!NOTE]
> You can use this procedure to download only robots.txt files that you previously uploaded through the Commerce authoring tools.

## Delete a robots.txt file

To delete a robots.txt file in Commerce, follow these steps:

1. Sign in to Commerce as a system admin.
1. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
1. Under **Tenant Settings**, select **Robots.txt**. A list of all the domains that are associated with your environment appears in the main part of the window.
1. Select **Manage** to delete a robots.txt file for a domain in your environment.
1. On the menu on the right, select the **Delete** button (the trash can symbol) next to the domain that is associated with the robots.txt file. A file browser window appears.
1. In the file browser window, browse to and select the robots.txt file that you want to delete for the domain, and then select **Open**. A warning message box appears.
1. In the message box, select **Delete** to confirm deletion of the robots.txt file.

> [!NOTE] 
> You can use this procedure to delete only robots.txt files that you previously uploaded through the Commerce authoring tools.

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
