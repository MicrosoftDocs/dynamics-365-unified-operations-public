---
# required metadata

title: Customize transactional emails by mode of delivery 
description: This topic describes how to set up custom email templates for specific notification types and modes of delivery
author: stuharg
manager: annbe
ms.date: 10/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Commerce, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-10-26
ms.dyn365.ops.version: Release 10.0.16

---

# Customize transactional emails by mode of delivery


[!include [banner](includes/banner.md)]


This topic describes how to set up custom email templates for specific notification types and modes of delivery



## Overview



Transactional emails can now be customized by a combination of notification type (e.g. order created, order packed, order invoiced etc), and mode of delivery (e.g. Overnight, in-store pickup, curbside pickup etc) which enables Retailers to provide order fulfillment experiences for their customers that are tailored to the order's mode of delivery. For example, the Order Packed event can be customized to provide curbside pickup instructions when customers choose curbside pickup, or shipping carrier and delivery information for customers who choose to have their order shipped.



Emails can be customized by mode of delivery for the following notification types:

| **Notification type**      | **Notes**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| Order cancellation         | New email  notification type                                 |
| Order created              |                                                              |
| Order confirmed            |                                                              |
| Order invoiced             | New email  notification type. This notification type can be used in place of the Order  shipped notification type, which will send a notification for any invoice  event with a shipped mode of delivery (i.e. not modes of delivery for pickup,  carryout and electronic) |
| Order picked               |                                                              |
| Order packed               |                                                              |
| Order ready for  pickup    | This notification  type is only customizable by mode of delivery if the Support for multiple  Pickup delivery modes feature switch is enabled. When enabled, this  notification type is functionally equivalent to the order packed notification  type. |
| Payment failed             |                                                              |
| Replacement order  created |                                                              |



NOTE

In order to leverage this feature, you will need to enable the **Customize transactional email templates by mode of delivery** feature switch, which is found in Workspaces -> Feature management in Dynamics 365 Headquarters. 



## Configure email templates for specific delivery modes

To customize transactional emails by mode of delivery for a specific notification type, follow the instructions below. NOTE: These instructions assume that you have already created and added your new, custom email templates to **Organization email templates**. Learn more about creating and uploading email templates in

[Create email templates for transactional events](email-templates-transactions.md)



1. In Dynamics 365 Headquarters, navigate to Commerce email notification profile
2. Select an existing notification type, or add a new one.
3. While the notification type is selected, click on **Configure modes of delivery**.
4. Click **+New** and select a mode of delivery in the dropdown in the mode of delivery row you just created
5. Select the email template you wish to map to the specific mode of delivery in the dropdown in the Email ID column for the row you just created
6. Check the checkbox in the Active column
7. Add additional modes of delivery and repeat steps 4 through 6, or click OK. 



NOTES:

- When more than one mode of delivery is present across lines in a sales order, the default template will be used. The default template is the one mapped to the notification type on the Commerce email notification profile page.
- If a sales order has a mode of delivery that has not been configured for a custom email template, the default email template will be used. 
 84  upload-serve-static-files.md 
Viewed
@@ -0,0 +1,84 @@
---
# required metadata

title: Upload and serve static files 
description: This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.
author: StuHarg
manager: annbe
ms.date: 10/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8
---
# Upload and serve static files

[!include [banner](../includes/banner.md)]

This topic describes how to upload a static file in Microsoft Dynamics 365 Commerce site builder and create a custom URL and file name that can be used to request the file.

## Overview

Some third party connectors require a file be hosted and served from the e-commerce site, which serves as a callback URL. These connectors expect the file to be returned by requests to a specific URL path and file name. This help topic explains how to upload and serve a static file on a Dynamics 365 Commerce e-commerce site, with a user-definable URL and file name. 

## Create a site URL that returns a static file

To create a site URL that returns a static file in Commerce site builder, follow these steps.

1. Go to **URLs** for your site.
1. Select **+ New \> New URL**.
2. In the **New URL** dialog box, select a Media Library URL.
3. In the **URL path** box, enter the URL path, including the file name.
4. Select **Next**, which will open the Media Library.
5. Select a previously uploaded file, or select **Upload** to upload a new file.
6. Select **Save**.

At this point, the URL you created is in draft state, and the file it points to will not be returned by that URL until you publish it. This allows you to validate that the correct data is being returned by the URL. 

## Validate an URL before publishing it

To validate an URL before publishing it, follow these steps.

1. Go to **URLs** for your site and select the URL you want to preview.
2. Below the **Edit** button in the properties pane on the right, select the correct URL link. This will launch a new browser window which will return a 404 error.
3. Add the `preview=inprogress` query string to the URL (for example, `https://yoursite.com/callback.html?preview=inprogress`).

The file you uploaded to the media library should be returned in the response. Once you have validated the URL, you can make it go live by going into the URLs section within your site, selecting the URL and clicking **Publish**.

## Update the file a URL points to

After a URL is published, you can change the file that it points to, or change the URL to a different type of resource such as an internal file or a redirect. 

## Update a URL

If you need to change the URL path that serves a file, or any other type of resource, you will need to create a new URL, map it to the existing file or other resource, and then unpublish and delete the old URL. 

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload videos](dam-upload-video.md)

[Upload files other than images and videos](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)
