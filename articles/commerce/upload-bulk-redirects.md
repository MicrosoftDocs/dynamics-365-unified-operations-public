---
title: Upload URL redirects in bulk
description: This article describes how to implement URL redirects in bulk by uploading a redirect comma-separate values (CSV) file in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 05/05/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2020-02-11
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
---

# Upload URL redirects in bulk

[!include [banner](includes/banner.md)]

This article describes how to implement URL redirects in bulk by uploading a redirect comma-separate values (CSV) file in Microsoft Dynamics 365 Commerce.

After you've finished creating a new e-commerce site in Dynamics 365 Commerce, and it's ready to go live, you must make the Domain Name System (DNS) switch from your old site to your new site. After you make this switch, the URLs for the new site will likely differ from the URLs for the old site. For specific URLs, traffic that uses the old URL can be redirected to the new URL. In this way, you ensure that site visitors reach the desired location. Redirects help prevent broken links for your customers and help you maintain your established search engine optimization (SEO) results.

Although redirects for individual links can be manually configured in DNS, manual configuration becomes tedious if multiple links must be redirected. To streamline the redirect process, Commerce provides the capability to upload a data file that contains bulk redirect mappings for your site. In the site settings in Commerce site builder, your system admin can upload and publish a CSV file that handles bulk URL redirects.

## Redirect CSV file

To handle URL redirects, Commerce supports a simple but specific CSV file. This file uses the following schema:

`source URL, target URL, redirect type, case sensitivity`

Here is an explanation of the elements of this schema:

- **Source URL**: The original URL that must be redirected.
- **Target URL**: The URL that users will be redirected to when they try to go to the source URL.
- **Redirect type**: Set this value to **301** or **302**, depending on the type of redirect that you want to use.

    - The **301** redirect type represents permanent redirects and is the most frequently used redirect type. It's the best option when you must maintain search engine optimization (SEO) rankings.
    - The **302** redirect type represents temporary redirects and is less frequently used. It's the best option when you must maintain link targeting during temporary maintenance or other non-permanent scenarios.

- **Case sensitivity**: Set this value to **true** if your source URL paths are case-sensitive. Case sensitivity will then be honored for the source URL paths. Set this value to **false** if case sensitivity isn't required. If you leave this value blank, the default value of **false** is used.

The following example shows a set of redirect rows in a redirect CSV file.

```plaintext
https://www.contoso.com/shop, https://www.fabrikam.com/allstores, 301, true

https://www.contoso.com/news, https://www.fabrikam.com/updates, 301, false

https://www.contoso.com/news, https://www.fabrikam.com/updates, 301
```

> [!IMPORTANT]
> The following rules must be followed. Otherwise, the bulk URL redirects won't work correctly.
>
> - **No header is allowed in the CSV file**: The first or topmost row must start with the first redirect row.
> - **There must be no circular entries**: The source URL in a row must not be used as the target URL in the same row. You must also avoid implementations where a target URL is linked back as a source URL, either in a different row of the CSV file or in a DNS redirect.
> - **Source and target URLs must be in valid URL format**: No spaces or invalid characters can be used in URLs.
> - **Source query string URLs are not supported**: Commerce won't run query strings that are provided as source.  However query string parameters for the destination may be used. 
> - **The CSV file must be in valid CSV format**: The CSV file must have comma-separated values, a separate line for each redirect, and valid file formatting, and it must have no header.

## Upload a redirect CSV file

Redirect CSV files can be uploaded by using Commerce site builder. The person who uploads a redirect CSV file to a site must be an admin for that site.

To upload a redirect CSV file, follow these steps.

1. In Commerce site builder, go to the site that will receive the bulk URL redirects.
1. Go to **Site settings \> General**.
1. Under **URL Redirect Mapping**, select **Upload**.
1. In File Explorer, browse to your CSV file, select it, and then select **Open**.
1. Under **URL Redirect Mapping**, set the option to **On** to activate the redirects.
1. On the command bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to take effect.

> [!IMPORTANT]
> Only one bulk redirect CSV file can be loaded and active per site at any time.

## Update an uploaded redirect CSV file

A previously uploaded redirect CSV file can be downloaded for reference. Alternatively, after the file is downloaded, it can be edited and then uploaded again.

To update an uploaded redirect CSV file, follow these steps.

1. In Commerce site builder, go to the site that will receive the bulk URL redirects.
1. Go to **Site settings \> General**.
1. Under **URL Redirect Mapping**, select **Download**.
1. Save the file to your local computer.
1. Edit the CSV file as appropriate, and then save it.
1. Under **URL Redirect Mapping**, select **Replace**.
1. In File Explorer, browse to the replacement CSV file, select it, and then select **Open**.
1. Under **URL Redirect Mapping**, set the option to **On** to activate the redirects.
1. On the command bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to take effect.

## Turn off bulk redirects

To turn off the bulk redirects in an uploaded redirect CSV file, follow these steps.

1. Create and save a new CSV file that has valid but nonexistent source and target URLs (for example, `https://www.com,https://www.com,301`).
1. In Commerce site builder, go to the site that will receive the bulk URL redirects.
1. Go to **Site settings \> General**.
1. Under **URL Redirect Mapping**, select **Replace**.
1. In File Explorer, browse to  your new CSV file, select it, and then select **Open**.
1. Under **URL Redirect Mapping**, set the option to **On** to activate the redirects. 
1. On the command bar, select **Save and Publish** to commit the changes. Allow up to 15 minutes for the redirects to stop working.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
