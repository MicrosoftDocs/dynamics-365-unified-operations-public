---
# required metadata

title: Add a favicon
description: This topic explains how to add a favicon to your site.
author: bicyclingfool
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

This topic explains how to add a favicon to your site.

## Overview

A favicon is a small image file that is displayed on the browser's tab, address bar, browser history, and bookmarks or favorites, among other places. It is a good idea to display a favicon on your site as it represents and reinforces your brand, and helps distinguish your site from other sites your customers visit. 

Although you can add favicons that support various sizes and file types to your site, this example will provide instructions for adding a single favicon. The location and process for adding additional favicons will be the same. 

### Upload a favicon to your site's assets collection

To upload a favicon to your site's assets collection, do the following.

1. Go to **Assets > Upload > Upload assets**.
1. Locate and select your favicon from your local file system.
1. Enter a title and click **OK**. 
1. Copy the public URL for the favicon from the property pane on the right.

[!NOTE]
If you don't select the **Publish assets after upload** option, you will need to return to **Assets** and publish the image manually later. 

### Create the HTML for the favicon image

To create the HTML for the favican image, do the following.

- Use the following HTML snippet, replacing the value of the href attribute ("Public_URL_for_your_favicon") with the public URL of your favicon copied earlier. 
  - &lt;link rel="shortcut icon" href="Public_URL_for_your_favicon" /&gt;

### Add the HTML for the favicon to the <head> tag of your pages

The procedure for adding a favicon to your site is the same one you would follow for adding any kind of HTML or script to the <head> tag of your site pages. Those steps are outlined in the [Adding script to your master templates](http://) topic. 

 

 

 

 
