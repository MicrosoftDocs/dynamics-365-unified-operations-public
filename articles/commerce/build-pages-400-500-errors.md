---
title: Build custom response pages for 4xx/5xx status code errors
description: This article describes how to build custom response pages for 4xx and 5xx status code errors by using the authoring tools in Microsoft Dynamics 365 Commerce.
author: brianshook
ms.date: 07/30/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Build custom response pages for 4xx/5xx status code errors

[!include [banner](includes/banner.md)]

This article describes how to build custom response pages for 4xx and 5xx status code errors by using the authoring tools in Microsoft Dynamics 365 Commerce.

If a request isn't successful, the server issues HTTP status code error responses. The 404 status code is captured and returned if a page isn't found, and the 500 status code is captured and returned if a server error occurs. In Dynamics 365 Commerce, application users can build custom status code error response pages that are shown to users for these status code error responses.

## Build a status code error response page

To start to build a status code error response page, follow these steps.

1. In your preferred web browser, sign in to Dynamics 365 Commerce. 
1. Select the site that you want to build a 4xx/5xx status code error response page for.

### Build the template

To build the template for the status code error response page, follow these steps.

1. Go to **Templates**.
1. Select **New** to create a page template.
1. In the **New Template** dialog box, under **Template Name**, enter a name for the new template, and then select **OK**.
1. Build the template, based on the structure that you want the status code error response page to have.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it. 

### Build the status code error response page

To build the status code error response page, follow these steps.

1. Go to **Pages**.
1. Select **New** to create a page.
1. In the **Choose a template** dialog box, select a template, and then, under **Page name**, enter a name for the status code error response page. Leave the **Page URL** field blank.
1. Build the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

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


[!INCLUDE[footer-include](../includes/footer-banner.md)]
