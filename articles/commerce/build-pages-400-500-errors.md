---
# required metadata

title: Build custom response pages for 4xx/5xx status code errors
description: This topic describes how to build custom response pages for 4xx and 5xx status code errors by using the authoring tools in Microsoft Dynamics 365 Commerce.
author: v-chgri
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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


[!include [banner](includes/banner.md)]

This topic describes how to build custom response pages for 4xx and 5xx status code errors by using the authoring tools in Microsoft Dynamics 365 Commerce.

## Overview

If a request isn't successful, the server issues HTTP status code error responses. The 404 status code is captured and returned if a page isn't found, and the 500 status code is captured and returned if a server error occurs. In Dynamics 365 Commerce, application users can build custom status code error response pages that are shown to users for these status code error responses.

## Build a status code error response page

To start to build a status code error response page, follow these steps.

1. In your preferred web browser, sign in to Dynamics 365 Commerce. 
1. Select the site that you want to build a 4xx/5xx status code error response page for.

### Build the template

To build the template for the status code error response page, follow these steps.

1. Go to **Templates \> New template**.
1. Name the new template.
1. Build the template, based on the structure that you want the status code error response page to have.
1. Check the template in, and publish it.

### Build the status code error response page

To build the status code error response page, follow these steps.

1. Go to **Pages \> New Page**.
1. Name the status code error response page, but do **not** set the **URL** field.
1. Build the page.
1. Check the page in, and publish it.

> [!NOTE]
> You can create separate status code error response pages for 4xx and 5xx status code errors. Alternatively, you can use the same general status code error response page for both error categories.

### Set up a redirect for the status code error response page

To set up a redirect for the status code error response page, follow these steps.

1. Go to **URLs \> New \> New Alias**, and select the status code error response page that you built earlier.
1. In the **Alias** field, enter either **default-4xx** or **default-5xx**, depending on the status code error response page that you're setting up a redirect for. These aliases must be published. Otherwise, the redirect won't work.
1. Select **OK** to commit the linking.

> [!NOTE]
> If you're using a single status code error response page for both error categories, repeat this procedure to link an alias for the other error category to the same page.

## Additional resources

[Work with templates](work-with-templates.md)

[Add a new site page](add-new-page.md)

[Create a page URL](create-page-url.md)
