---
# required metadata

title: Add a favicon
description: This topic explains how to add a favicon to your site
author: StuHarg
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Consumer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: StuHarg
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 
---

# Add a favicon

This topic explains how to add a favicon to your site

A favicon is a small image file that is displayed in the browser's tab, address bar, browser history, bookmarks or favorites, among other places. It is a good idea to display a favicon on your site as it represents and reinforces your brand, and helps distinguish your site from other sites your customers visit. 

Although you can add favicons that support various sizes and file types to your site, this example will provide instructions for adding a single favicon. The location and process for adding additional favicons  will be the same. 



### Upload your favicon to your site's assets collection

1. Navigate to your site's assets by clicking on the **Assets** menu in the site authoring environment
2. Click **Upload** and select **Upload assets**
3. Locate and select your favicon from your local file system
4. Provide a title and click **Ok**. NOTE: If you don't select the Publish assets after upload option, you will need to return to your Assets and publish this image manually at a later time. 
5. Copy the Public URL for the favicon from the property pane on the right



### Create the HTML for the favicon image

Use the following HTML snippet, replacing the value of the href attribute with the Public URL of your favicon. <link rel="shortcut icon" href="Public_URL_for_your_favicon" />



### Add the HTML for the favicon to the <head> tag of your pages

The procedure for adding a favicon to your site is the same one you would follow for adding any kind of HTML or script to the <head> tag of your sites pages. Those steps are outlined in the [Adding script to your master templates](http://) topic. 

 

 

 

 
