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
[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

# Build custom response pages for 4xx/5xx status code errors 

This topic describes how to build custom response pages for 4xx and 5xx status code errors using the authoring tools in Dynamics 365 Retail.

## Overview

A server will issue HTTP response status code errors when a client request is not successful. All 4xx categorical status codes are client error responses, and all 5xx categorical status codes are server error responses. In Dynamics 365 Retail, application users can build custom response pages to display to end users in the event of 4xx or 5xx status code error responses.

## Build a status code error response page
To begin building a status code error response page, do the following.

1. Log in to the Microsoft Dynamics 365 Retail Authoring Tools in your preferred browser. 
1. Select the site for which you will be building the 4xx/5xx status code error response page. 

#### Build the master template

To build the master template, do the following.

1. From the site menu, select **Master Template**.
1. Create a new master template.
1. Name the master template.
1. Build the template according to how you want the error page to be structured.
1. Check in the master template.
1. Publish the master template.

#### Build the error page

To build the error page, do the following.

1. From the site menu, select **Pages**.
1. Click **New Page**. 
1. Name the error page. Do not fill in the **URL** field at this time. 
1. Build out the page in the Authoring Tool as you want presented to end users.
1. Check in the error page.
1. Publish the error page.

[!Note] You can create separate error pages for 4xx and 5xx status code errors, or use the same general error page for both errors.

#### Set up a redirect for the error page

To set up a redirect for the error page, do the following.

1. From the site menu, select **URLs**.
1. Go to **New > New Alias** and select the new error page.
1. For the alias, enter *default-4xx* or *default-5xx*, depending on which error page you are setting up.
1. Click **OK** to commit the linking.

[!Note] If using a single page instance for both error categories, repeat the process and link a new alias to the same page.

