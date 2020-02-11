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

**Source URL, Target URL, Redirection Type (301/302), case sensitivity (default false)**

To review these fields further:

- **Source URL**: This is the original URL from the previous site (or previously active)
- **Target URL**: This is the target URL that viewers landing on the Source URL will be directed (the new URL)
- **Redirection Type**: Use "301" or "302" dependent on the type of redirect you intend to use. 
  - **301** redirects signal permanent redirects, and are the most common redirect type. This is the best approach for maintaining SEO rankings.
  - **302** redirects signal temporary redirects, and are less commonly used. This code is best for temporary maintenance or other non-permanent scenarios to maintain link targeting.
- **case sensitivity**: Set this to "true" if your Source URL paths are case-sensitive. If true, case sensitivity will be honored for paths of the Source URL field. Leave this field blank or set to "false" if case sensitivity is not needed. The default (leaving blank) will be false.

So a sample set of redirect rows may look like the following:

*https://www.oldsite.com/shop, https://www.newsite.com/allstores, 301*

*https://www.oldsite.com/news, https://www.newsite.com/updates, 301*

**<u>Important:</u>** The following **<u>must</u>** be followed in order for the bulk redirects to work correctly:

- **<u>No header</u>** in the CSV file. The first or topmost row must start with the first redirect row
- No circular entries - a source must not also be repeated as the target in the same row. Additionally, avoid a data set where a target may link back as a source via multiple rows (or redirects).
- The source and target data must be valid URL format (no spaces or invalid characters).
- **No Query String URLs** supported. The current solution will not execute query strings provided as source or target URLs.
- CSV must be a valid CSV format. Use comma-separated, no header, new-line valid CSV data and file formatting.

## Upload the CSV

The bulk redirect CSV can be uploaded in the Commerce site builder Tool. User must be an administrator for the site they are uploading the bulk redirect CSV. 

From Home, navigate to the Site that will receive the bulk URL redirects.

Go to **Site Settings > General** in the left hand menu.

Within the General page, the section labeled "URL Redirect Mapping" will be utilized.

Have your URL redirect mapping CSV accessible on your machine. In the "URL Redirect Mapping" section, select the "Upload" button. A file picker dialogue will launch. Navigate to and select your bulk mapping CSV file and select 'Open'.

Once the file is uploaded successfully, select the Toggle button to "On" to activate the re-directs. Select the **Save & Publish** button at the top of the Site Settings General page in order to commit the upload and toggle changes. The re-directs will now be live (allow up to 15 minutes to see traffic redirecting).

Only one CSV per site can be loaded and active at any given time.

## Update the CSV file

An uploaded URL redirects CSV file can be downloaded for reference or editing.

In order to download the currently uploaded CSV, navigate to your Site and go to **Site Settings > General** in the left hand menu.

Within the "URL Redirect Mapping" section, select the "Download" button. (This button will be grayed out if no CSV has been uploaded). A save file dialogue will be prompted to save the file to your machine.

If making additions, deletions, or edits to the CSV; once completed, use the "Replace" button (which should show in place of the original 'Upload' button) to upload the edited file. Notice that upon re-upload, the Toggle will switch back to "Off".  Change the Toggle to "On" and **Save & Publish** the General settings page to commit these changes. This will then activate the newly uploaded file. Again, allow up to 15 minutes for the changes to occur. 

## Turn off the bulk redirect mappings

If a bulk redirect CSV has been uploaded and is active; to turn the redirects off- go to **Site Settings > General** and select the "Replace" button. Upload a new CSV with valid but non-existent Source and Target URLs. (Example: 'https://www.com,https://www.com,301'. Set the Toggle to "On" and click **Save & Publish** on the General settings page to commit the changes.
