---
# required metadata

title: Add a favicon
description: This topic explains how to add a favicon to your site.
author: bicyclingfool
manager: annbe
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: StuHarg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Add a favicon


[!include [banner](includes/banner.md)]

This topic explains how to add a favicon to your site.

## Overview

A favicon is a small graphics file that is shown on a web browser tab, in the Address bar, in the browsing history, and in bookmarks or favorites, among other places. We recommend that you add a favicon to your site, because it represents and reinforces your brand, and helps distinguish your site from other sites that your customers visit.

Although you can add multiple favicons of various sizes and file types to your site, this topic shows how to add a single favicon. However, the same process and location are used to add more favicons.

## Upload a favicon to your site's asset collection

To upload a favicon to your site's asset collection, follow these steps.

1. Go to **Assets \> Upload \> Upload assets**.
1. Find and select the favicon on your local file system.
1. Enter a title, and then select **OK**. 
1. In the property pane on the right, copy the public URL of the favicon.

> [!NOTE]
> If you don't select the **Publish assets after upload** option, you must return to **Assets** page and manually publish the favicon later.

## Create the HTML for the favicon

To create the HTML for the favicon, use the following HTML snippet. For the **href** attribute, replace **"Public\_URL\_for\_your\_favicon"** with the public URL that you copied earlier.

`<link rel="shortcut icon" href="Public_URL_for_your_favicon">`

## Add the HTML for the favicon to the \<head\> element of your pages

To add a favicon to your site, use the same procedure that is used to add any type of HTML or script to the **\<head\>** element of your site pages.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a welcome message](add-welcome-message.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

