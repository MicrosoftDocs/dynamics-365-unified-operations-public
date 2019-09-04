---
# required metadata

title: Build custom response pages for 4xx/5xx status code errors
description: This topic describes how to build custom response pages for 4xx and 5xx status code errors using the authoring tools in Dynamics 365 Retail.
author: brshoo
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
ms.reviewer: josaw
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Build custom response pages for 4xx/5xx status code errors 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to build custom response pages for 4xx and 5xx status code errors using the authoring tools in Dynamics 365 Retail.

## Overview

A server will issue HTTP response status code errors when a request is not successful. The 404 and 500 status codes are captured and returned in the case of a page not found our server error. In Dynamics 365 Retail, application users can build custom response pages to display to end users in the event of these status code error responses.

## Build a status code error response page
To begin building a status code error response page, do the following.

1. Sign in to Dynamics 365 Retail Authoring Tools in your preferred browser. 
1. Select the site for which you will be building the 4xx/5xx status code error response page. 

#### Build the template

To build the template, do the following.

1. Go to **Templates > New template**.
1. Name the new template.
1. Build the template according to how you want the error page to be structured.
1. Check in and publish the template.

#### Build the error page

To build the error page, do the following.

1. Go to **Pages > New Page**.
1. Name the error page. Do not fill in the **URL** field at this time. 
1. Build out the error page.
1. Check in and publish the error page.

[!NOTE]
You can create separate error pages for 4xx and 5xx status code errors, or use the same general error page for both errors.

#### Set up a redirect for the error page

To set up a redirect for the error page, do the following.

1. Go to **URLs > New > New Alias** and select the new error page.
1. In the **Alias** field, enter *default-4xx* or *default-5xx* depending on which error page you are setting up. These aliases must be published to work actively.
1. Click **OK** to commit the linking.

[!NOTE]
If using a single page instance for both error categories, repeat the process and link a new alias to the same page.

