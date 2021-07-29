---
# required metadata

title: Page caching
description: This topic describes how to configure pages to be cached. 
author: samjarawan
ms.date: 07/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Page Caching

[!include [banner](../includes/banner.md)]

This topic describes how to configure pages to be cached.

Page caching (available in release 10.0.21 (Online SDK version 1.31.3 or greater)) allows e-commerce pages to be cached on the server.  Cached pages can then be served to web site customers, signficantly increasing performance time. You can choose which pages to cache and how long to cache them in the site builder tool on a [page](../modify-existing-page.md) or by configuring a [template](../templates-layouts-overview.md) that enables page caching and applying that template across multiple different pages.
 
The page cache works by generating the entire page content and saving the content for a particular route for a set time. When another user accesses the same page, instead of computing the page and returning the response, the cached page is immediately returned to the user.  Cached pages can become stale, so it is important to understand when and where to use page caching.
 
Some pages need to ensure they stay as fresh as possible with dynamic data such as product prices, and may call many [data actions](data-actions.md) when constructing the page. Page caching can still be leveraged for these pages by setting a lower cache timeout to ensure the page is frequently refreshed to serve the most accurate content to your e-commerce customers.

## Enable page caching

To get started using page caching the feature must be turned on at the site level.


![Module configuration fields in the authoring tools.](media/module-config-fields.png)

## Add new module configuration fields
