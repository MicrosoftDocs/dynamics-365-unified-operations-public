---
# required metadata

title: Upload URL redirects in bulk 
description: This topic describes how to implement URL redirects in bulk by uploading a redirect CSV file in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 02/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2020-02-11
ms.dyn365.ops.version: 

---

# Upload URL redirects in bulk

[!include [banner](includes/banner.md)]

This topic describes how to implement URL redirects in bulk by uploading a redirect CSV file in Microsoft Dynamics 365 Commerce.

## Overview

When creating your new e-commerce site on Dynamics 365 Commerce, the URLs from your previous site will likely differ once you make the Domain Name System (DNS) switch when going live with the new Commerce-built site. For specific URLs, you can redirect traffic using the old URL to the new URL, ensuring that your site visitors land in the desired location. Redirects help avoid broken links for your customers and maintain your established SEO results. Although redirects can be configured in DNS manually for single links, when multiple links need to be redirected manual configuration becomes tedious. To streamline the redirect process, Commerce has the capability to upload a data file with bulk redirect mappings for your site. Within the site builder site settings, your system administrator can upload and publish a comma-separated values (CSV) file that handles these link redirects in bulk.

## Redirect CSV file

Commerce supports a simple yet specific CSV file to handle the redirect URLs. 

The schema of the CSV is as follows:

``source URL, target URL, redirect type (301/302), case sensitivity (default false)``

- **Source URL**: This is the original URL to be redirected.
- **Target URL**: This is the target URL that users will be redirected to from the source URL. 
- **Redirect type**: Use "301" or "302" dependent on the type of redirect you intend to use. 
  - The **301** redirect type denotes permanent redirects, and is the most common redirect type. This is the best approach for maintaining SEO rankings.
  - The **302** redirect type denotes temporary redirects, and is less commonly used. This redirect type is best used to maintain link targeting for temporary maintenance or other non-permanent scenarios.
- **Case sensitivity**: Set this value to "true" if your source URL paths are case sensitive. If set to "true," case sensitivity will be honored for source URL path. If set to "false" or left blank, case sensitivity is not needed. If left blank, the default value is false.

An example set of redirect rows may look like the following:

``https://www.oldsite.com/shop, https://www.newsite.com/allstores, 301, true``

``https://www.oldsite.com/news, https://www.newsite.com/updates, 301, false``

``https://www.oldsite.com/news, https://www.newsite.com/updates, 301``

> [!IMPORTANT]
> The following rules must be followed in order for the bulk redirects to work correctly.

- **No header in the CSV file**: The first or topmost row must start with the first redirect row.
- **No circular entries**: A source URL must not be used as the target in the same row. Also, avoid implementations where a target URL may link back as a source, either in a different row of the CSV file or a DNS redirect.
- **Source and target URLs must be in valid URL format**: No spaces or invalid characters can be used in URLs.
- **No query string URLs are supported**: Commerce will not execute query strings provided as source or target URLs.
- **CSV file must be in valid CSV format**: CSV file must have comma-separated values, separate lines for each redirect, no header, and valid file formatting.

## Upload a redirect CSV file

A redirect CSV file can be uploaded using Commerce site builder. The uploader must be an administrator for the site they are uploading the redirect CSV file to.

To upload a redirect CSV file, follow these steps.

1. In Commerce site builder, navigate to the site that will receive the bulk URL redirects.
1. Go to **Site settings \> General**.
1. Under **URL Redirect Mapping**, select **Upload**. 
1. In File Explorer, browse to and select your CSV file, and then select **Open**.
1. Under **URL Redirect Mapping**, set the toggle key to **On** to activate the redirects. 
1. On the commmand bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to take effect.

> [!IMPORTANT]
> Only one bulk redirect CSV file can be loaded and active per site at any given time.

## Update an uploaded redirect CSV file

A previously-uploaded redirect CSV file can be downloaded for reference or editing and reupload.

To update an existing uploaded CSV file, follow these steps.

1. In Commerce site builder, navigate to the site that will receive the bulk URL redirects.
1. Go to **Site settings > General**.
1. Under **URL Redirect Mapping**, select **Download**. 
1. Save the file to your local machine.
1. Edit the CSV file as appropriate and save it when done.
1. Under **URL Redirect Mapping**, select **Replace**. 
1. In File Explorer, browse to and select the replacement CSV file, and then select **Open**
1. Under **URL Redirect Mapping**, set the toggle key to **On** to activate the redirects. 
1. On the command bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to take effect.

## Turn off bulk redirects

To turn off bulk redirects in an uploaded CSV file, follow these steps.

1. Create and save a new CSV file with valid but non-existent source and target URLs. (For example, ``https://www.com,https://www.com,301``).
1. In Commerce site builder, navigate to the site that will receive the bulk URL redirects.
1. Go to **Site settings > General**.
1. Under **URL Redirect Mapping**, select **Replace**. 
1. In File Explorer, browse to and select your new replacement CSV file, and then select **Open**
1. Under **URL Redirect Mapping**, set the toggle key to **On** to activate the redirects. 
1. On the command bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to stop working.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Create an e-Commerce site](create-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
