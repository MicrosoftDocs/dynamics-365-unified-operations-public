---
# required metadata

title: Upload bulk URL redirect mappings 
description: This topic describes how to upload a mapping reference file to redirect URLs in Microsoft Dynamics 365 Commerce.
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

# Upload bulk URL redirect mappings

[!include [banner](includes/banner.md)]

This topic describes how to upload a mapping reference file to redirect URLs in Microsoft Dynamics 365 Commerce.

This topic describes the process of uploading a CSV mapping file to redirect your web traffic from previous site URLs to your updated Commerce site URLs. This article covers the CSV format, the upload process, and updating process for handling bulk URL redirects.

## Overview

When creating your new e-commerce site on Dynamics 365 Commerce, the URLs from your previous site will likely differ once you make the Domain Name System (DNS) switch with your domain when going live on the new Commerce-built site. For specific URLs, you can redirect traffic using the old URL to the new URL, ensuring that your site visitors land in the desired location. Redirects help avoid broken links for your customers and maintain your established SEO results. Although redirects can be configured in DNS manually for a single link, when multiple links need to be redirected manual configuration becomes tedious. Commerce solves this issue with the capability to upload a data file with bulk redirect mappings for your site. Within the site builder site settings, your system admin can upload and publish a comma-separated values (CSV) file to handle these link redirects in bulk.

## The redirect CSV file

Commerce supports a simple yet specific CSV file to handle the redirect URLs. This section will cover the schema and rules of the CSV file. 

The schema of the CSV is as follows:

``source URL, target URL, redirect type (301/302), case sensitivity (default false)``

- **Source URL**: This is the original URL to be redirected.
- **Target URL**: This is the target URL that users will be redirected to from the source URL. 
- **Redirect type**: Use "301" or "302" dependent on the type of redirect you intend to use. 
  - The **301** redirect type denotes permanent redirects, and are the most common redirect type. This is the best approach for maintaining SEO rankings.
  - The **302** redirect type denotes temporary redirects, and are less commonly used. This redirect type is best used to maintain link targeting for temporary maintenance or other non-permanent scenarios.
- **Case sensitivity**: Set this value to "true" if your source URL paths are case sensitive. If true, case sensitivity will be honored for source URL path. If "false" or left blank, case sensitivity is not needed. If left blank, the default value is false.

An example set of redirect rows may look like the following:

``https://www.oldsite.com/shop, https://www.newsite.com/allstores, 301``
``https://www.oldsite.com/news, https://www.newsite.com/updates, 301``

> [!IMPORTANT]
> The following rules must be followed in order for the bulk redirects to work correctly.

- **No header in the CSV file**: The first or topmost row must start with the first redirect row.
- **No circular entries**: A source URL must not be used as the target in the same row. Also, avoid implementations where a target may link back as a source, either in a different row of the CSV file or a DNS redirect.
- **Source and target URLs must be in valid URL format**: No spaces or invalid characters can be used in URLs.
- **No query string URLs are supported**: Commerce will not execute query strings provided as source or target URLs.
- **CSV file must be in valid CSV format**: CSV file must have comma-separated values, separate lines for each redirect, no header, and valid file formatting.

## Upload a bulk redirect CSV file

The bulk redirect CSV file can be uploaded in the Commerce site builder tool. The uploader must be an administrator for the site they are uploading the bulk redirect CSV file to.

To upload a CSV file, follow these steps.

From Home, navigate to the Site that will receive the bulk URL redirects.

Go to **Site settings \> General** in the left hand menu.

Within the General page, the section labeled "URL Redirect Mapping" will be utilized.

Have your URL redirect mapping CSV accessible on your machine. In the "URL Redirect Mapping" section, select the "Upload" button. A file picker dialogue will launch. Navigate to and select your bulk mapping CSV file and select 'Open'.

Once the file is uploaded successfully, select the Toggle button to "On" to activate the re-directs. Select the **Save & Publish** button at the top of the Site Settings General page in order to commit the upload and toggle changes. The re-directs will now be live (allow up to 15 minutes to see traffic redirecting).

> [!IMPORTANT]
> Only one bulk redirect CSV file can be loaded and active per site at any given time.

## Update the CSV file

An uploaded URL redirects CSV file can be downloaded for reference or editing.

In order to download the currently uploaded CSV, navigate to your Site and go to **Site Settings > General** in the left hand menu.

Within the "URL Redirect Mapping" section, select the "Download" button. (This button will be grayed out if no CSV has been uploaded). A save file dialogue will be prompted to save the file to your machine.

If making additions, deletions, or edits to the CSV; once completed, use the "Replace" button (which should show in place of the original 'Upload' button) to upload the edited file. Notice that upon re-upload, the Toggle will switch back to "Off".  Change the Toggle to "On" and **Save & Publish** the General settings page to commit these changes. This will then activate the newly uploaded file. Again, allow up to 15 minutes for the changes to occur. 

## Turn off the bulk redirect mappings

If a bulk redirect CSV has been uploaded and is active; to turn the redirects off- go to **Site Settings > General** and select the "Replace" button. Upload a new CSV with valid but non-existent Source and Target URLs. (Example: 'https://www.com,https://www.com,301'. Set the Toggle to "On" and click **Save & Publish** on the General settings page to commit the changes.
